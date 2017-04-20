# compass-config
<h6>compass config</h6>

### 使用说明
* 在安装好compass及compass-normalize(gem install compass-normalize)后，对新建的project中的config进行如下配置

````
require 'compass/import-once/activate'
require 'compass-normalize'
# Require any additional compass plugins here.
````
* 配置所有路径地址
````
# Set this to the root of your project when deployed:
http_path = "/"
css_dir = "css"
sass_dir = "sass"
images_dir = "images"
javascripts_dir = "js"
````
* 设置编译后的css格式:
    1. :expanded 保留原格式
    2. :nested 样式名在前，一个名字一行，每个定义项各一行
    3. :compact 简介模式，一个样式一行
    4. :compressed 压缩模式，所有代码在一行上

````
# You can select your preferred output style here (can be overridden via the command line):
output_style = :compact
````

* 通过compass帮助工具打开资源相对路径功能
````
# To enable relative paths to assets via compass helper functions. Uncomment:
relative_assets = true
````
* 生成'//'注释
````
# To disable debugging comments that display the original location of your selectors. Uncomment:
line_comments = false
````
* 设置sass的语法缩进
````　
# If you prefer the indented syntax, you might want to regenerate this
# project again passing --syntax sass, or you can uncomment this:
# preferred_syntax = :sass
# and then run:
# sass-convert -R --from scss --to sass sass scss && rm -rf sass && mv scss sass
````
* 使用compass的图片精灵的时候，生成的图片名为所建文件夹的名字，并不再加随机字符
````
# Get the directory that this configuration file exists in
on_sprite_saved do |filename|
  if File.exists?(filename)
    # FileUtils.cp filename, filename.gsub(%r{-s[a-z0-9]{10}\.png$}, '.png')
    FileUtils.mv filename, filename.gsub(%r{-s[a-z0-9]{10}\.png$}, '.png')
  end
end

on_stylesheet_saved do |filename|
  if File.exists?(filename)
    css = File.read filename
    File.open(filename, 'w+') do |buffer|
      buffer << css.gsub(%r{-s[a-z0-9]{10}\.png}, '.png')
    end
  end
end
````
