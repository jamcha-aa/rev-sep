# rev-sep

ox-md (org-mode to markdown) automatically replaces "---" (YAML separator) to "&#x2014;" (dash).

This program resurrects "---". If you are annoying such ox-md  thoughtfulness, try this.

## Code
```
(defun rev-sep (filename)
  (interactive "sInput Name: ")
  (with-temp-buffer
    (insert (replace-regexp-in-string "\&\#x2014;" "---" (f-read-text filename)))
    (write-file filename)))
```

## Usage

**M-x rev-sep** then input _markdown file_.

(c) 2018 jamcha (jamcha.aa@gmail.com).

This program is licensed under the NYSL. (http://kmonos.net/NYSL/index.en.html)
