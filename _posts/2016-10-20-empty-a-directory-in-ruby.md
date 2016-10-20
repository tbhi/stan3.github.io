---
layout: post
---
I find this a useful one liner to empty a directory (but keep forgetting it!):

    FileUtils.rm_rf("#{dir_path}/.", secure: true)

from [stackoverflow](http://stackoverflow.com/a/8224531)
