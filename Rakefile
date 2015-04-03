# Set default task
task :default => :deploy

# rake deploy
desc "Deploy the site to a remote git repo"
task :deploy do
    system "git add -A"
    system "git commit -m \'publication\'"
    system "git push"
end
