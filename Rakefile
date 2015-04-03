# Set default task
task :default => :deploy

# rake build
desc "Build the site"
task :build do
  system "jekyll build"
end

# rake deploy
desc "Deploy the site to a remote git repo"
task :deploy do
    system "git add -A"
    system "git commit -m publication"
    system "git push"
    system "open http://fguada.github.io"
end
