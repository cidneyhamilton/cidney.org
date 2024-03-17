---
layout: post
title: 'Automating creating a Jekyll post'
date: '2023-10-18 14:22:19 -0400'
tags: tooling
---
I'm trying to get myself to write more. So I just added a function (based on [this gist](https://gist.github.com/tpanum/f1bcd76cfdc6d3f3b28a) to automate adding a new timestamped post to my drafts folder.

It looks like this:

```
(setq blog-home "~/Dev/cidney.org")

(defun create-jekyll-draft
  (title)
  "Creates a new buffer and file for a blog post"
  (interactive "Title of blog post: ")
  (let
    ((filename
       (concat
         (format-time-string "%Y-%m-%d-")
         (replace-regexp-in-string " " "-"
           (downcase
             (replace-regexp-in-string "[^0-9a-zA-Z ]" "" title))))))
    (switch-to-buffer
      (generate-new-buffer filename))
    (insert
      (concat
        (mapconcat 'identity
          '("---" "layout: post")
          "\n")
        "\n" "title: '" title "'\n" "date: '"
        (format-time-string "%Y-%m-%d %H:%M:%S %z")
        "'\n" "---\n"))
    (write-file
      (concat blog-home "/_drafts/" filename ".md"))))
```

Once run I have a new file in my _drafts folder, and don't have to duplicate the title or timestamp when creating a file and inserting front matter.

Will this help? I'll find out.