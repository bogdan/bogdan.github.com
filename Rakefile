task :dev do
  c = Thread.new do
    `compass watch --sass-dir css --css-dir css`
  end
  j = Thread.new do
    `jekyll --server`
  end
  sleep(1)
  c.join
  j.join
end
