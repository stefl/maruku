require 'rubygems'
Gem::manage_gems
require 'rake/gempackagetask'

require 'maruku_gem'


task :default => [:package]

Rake::GemPackageTask.new($spec) do |pkg|
  pkg.need_zip = true
  pkg.need_tar = true
end

PKG_NAME = 'maruku'
PKG_FILE_NAME = "#{PKG_NAME}-#{PKG_VERSION}"
RUBY_FORGE_PROJECT = PKG_NAME
RUBY_FORGE_USER = 'andrea'

RELEASE_NAME  = PKG_VERSION
RUBY_FORGE_GROUPID = '2795'
RUBY_FORGE_PACKAGEID = '3292'

desc "Publish the release files to RubyForge."
task :release => [:gem, :package] do
  files = ["gem", "tgz", "zip"].map { |ext| "pkg/#{PKG_FILE_NAME}.#{ext}" }
  system("rubyforge login --username #{RUBY_FORGE_USER}")
  files.each do |file|
    system("rubyforge add_release #{RUBY_FORGE_GROUPID} #{RUBY_FORGE_PACKAGEID} \"#{RELEASE_NAME}\" #{file}")
  end
end