# rev-sep

This program modifies symbols of ox-md (org-mode to markdown) converted markdown files.

#### Modification list
- dash (&mdash;) to triple hyphens (---)
  + This option might be useless when you add **#+OPTION: -:nil** to your preambles.
- sidebar\\_label to sidebar_label
  + This option is especially for Docusaurus. 

## Code
```
(require 'xah-replace-pairs)
(defun rev-sep (filename)
  (interactive "sInput Name: ")
  (with-temp-buffer
    (insert (f-read-text filename))
    (xah-replace-regexp-pairs-region (point-min) (point-max)
                                     '(
                                       ("\&\#x2014;" "---")
                                       ("sidebar\\\\_label" "sidebar_label"))) 
    (write-file filename)))
```

## Usage

Add **#+OPTIONS: ^:{}** to your preambles.

**M-x rev-sep** then input _markdown file_.

(c) 2018 jamcha (jamcha.aa@gmail.com).

This program is licensed under the NYSL. (http://kmonos.net/NYSL/index.en.html)
