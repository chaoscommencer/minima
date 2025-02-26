# frozen_string_literal: true

source "https://rubygems.org"
gemspec

JEKYLL_GEM_NAME = "jekyll"
JEKYLL_GEM_VERSION = ENV["JEKYLL_VERSION"]
unless JEKYLL_GEM_VERSION.nil?
    gem JEKYLL_GEM_NAME, JEKYLL_GEM_VERSION
end

# NOTE: Gem::Version.new required to support Ruby version 2.7 in which
# RUBY_VERSION constant is a string instead of a version object
if Gem::Version.new(RUBY_VERSION) >= Gem::Version.new('3.0.0')
    # Support for encoding and decoding binary data using a Base64
    # representation.
    # Include base64 (no-longer included by default from Ruby 3.4.0 onward).
    # WARNING: base64 was loaded from the standard library, but is not part of
    # the default gems starting from Ruby 3.4.0.
    # Source: vendor/bundle/ruby/3.4.0/gems/safe_yaml-1.0.5/lib/safe_yaml/transform.rb:1
    # You can add base64 to your Gemfile or gemspec to silence this warning.
    # Failing to include the base64 gem as described above further causes...
    # ERROR: bundler: failed to load command: jekyll (vendor/bundle/ruby/3.4.0/bin/jekyll)
    # /opt/hostedtoolcache/Ruby/3.4.2/x64/lib/ruby/3.4.0/bundled_gems.rb:82:in
    # 'Kernel.require': cannot load such file -- base64 (LoadError)
    gem 'base64', '~> 0.2.0'

    # This library provides arbitrary-precision decimal floating-point number
    # class.
    # WARNING: bigdecimal was loaded from the standard library, but is not part
    # of the default gems starting from Ruby 3.4.0.
    # Source: vendor/bundle/ruby/3.4.0/gems/liquid-4.0.4/lib/liquid/standardfilters.rb:2
    # You can add bigdecimal to your Gemfile or gemspec to silence this warning.
    # Failing to include the base64 gem as described above further causes...
    # ERROR: bundler: failed to load command: jekyll (vendor/bundle/ruby/3.4.0/bin/jekyll)
    # /opt/hostedtoolcache/Ruby/3.4.2/x64/lib/ruby/3.4.0/bundled_gems.rb:82:in
    # 'Kernel.require': cannot load such file -- bigdecimal (LoadError)
    gem 'bigdecimal', '~> 3.1', '>= 3.1.9'

    # Include logger (no-longer included by default from Ruby 3.5.0 onward).
    # WARNING: logger was loaded from the standard library, but will no longer
    # be part of the default gems starting from Ruby 3.5.0.
    # You can add logger to your Gemfile or gemspec to silence this warning.
    gem 'logger', '~> 1.6', '>= 1.6.6'
end
