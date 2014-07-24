require "bundler/setup"
require "yaml"
require "stringex"
require "date"

$CREDS = false
if File.exists? "./credentials.rb"
  require "./credentials"
  $CREDS = true
end


task :default => :watch

USER_PREFS_FILE = "#{ENV['HOME']}/.kod-webbox-io-prefs.yml"
DATE_FORMAT = "%Y-%m-%d"
NOW = Time.now.strftime(DATE_FORMAT)

if File.exists?(USER_PREFS_FILE)
  USER_INFO = YAML.load_file(USER_PREFS_FILE)
else
  USER_INFO = nil
end


# rake watch
# rake watch[number]
# rake watch["drafts"]
desc "Ön izleme, Development Sunucusu (post limiti ve draft özelliği)"
task :watch, :option do |t, args|
  option = args[:option]
  if option.nil? or option.empty?
    system "jekyll serve --watch"
  else
    if option == "drafts"
      system "jekyll serve --watch --drafts"
    else
      system "jekyll serve --watch --limit_posts #{option}"
    end
  end
end

desc "Yeni hile post et"
task :post, :title do |t, args|
  raise "Lütfen -rake setup- ile kullanıcı bilgilerinizi düzenleyin!" if USER_INFO.nil?
  
  title = args[:title] ? args[:title] : "yeni-post"
  post_file = "_posts/#{NOW}-#{title.to_url}.md"
  
  output = ["---"]
  output << "title: #{title}"
  output << "layout: post"
  output << "tags: []"
  output << "date: #{Time.now.strftime("%b %d, %Y %H:%M")}"
  output << "published: true"
  output << "writer:"
  output << "  full_name: #{USER_INFO['full_name']}"
  output << "  www: #{USER_INFO['www']}"
  output << "---"
  
  File.write post_file, output.join("\n")
  puts "Yeni post edit edilmek için hazır: #{post_file}"
end


desc "İlk çalıştırma (Ayarlar)"
task :setup do
  
  os_name = `uname`.chomp
  user_fullname = ""
  user_www = "http://kod.webbox.io"
  if os_name == "Darwin"
    whoami = `whoami`.chomp
    user_fullname = `finger #{whoami} | awk -F: '{ print $3 }' | head -n1 | sed 's/^ //'`.chomp
    puts "Lütfen Adınız, Soyadınızı girin: (#{user_fullname} ise enter yapın) ?"
    user_input_fullname = STDIN.gets.chomp
    unless user_input_fullname.empty?
      user_fullname = user_input_fullname
    end
  else
    puts "Lütfen Adınızı, Soyadınızı girin:"
    user_input_fullname = STDIN.gets.chomp
    if user_input_fullname.empty?
      user_fullname = "İsimsiz"
    else
      user_fullname = user_input_fullname
    end
  end
  
  puts "Lütfen kişisel web sayfanızı girin (Twitter olabilir, websiteniz olabilir) ? Örnek: http://twitter.com/vigobronx"
  user_input_www = STDIN.gets.chomp
  user_www = user_input_www unless user_input_www.empty?
  
  
  user_data = {
    "full_name" => user_fullname,
    "www" => user_www
  }
  
  f = File.new USER_PREFS_FILE, "w"
  f.write user_data.to_yaml
  f.close

  puts "Ad, Soyad: #{user_fullname}"
  puts "Web: #{user_www}"
  puts "Artık post yapmaya başlıyabilirsiniz!"
end


desc "Deploy to webBox.io"
task :deploy do
  if $CREDS
    ENV["JEKYLL_ENV"] = "production"
    system "jekyll build"
    system "rsync -av _site/ #{DEPLOY_DESTINATION}"
    puts "Deploy completed..."
  else
    puts "You need credentials.rb file..."
  end
end
