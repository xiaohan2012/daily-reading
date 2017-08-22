# goal

replace `\`....\`` into `$\`....\`$`

# code in emacs lisp

```lisp
(defun katex-mathify ()
  (interactive)
  (goto-char (point-min))
  (replace-regexp "\\([^$\n]?\\)`\\([^$]*?\\)`\\([^$]\\)" "\\1$`\\2`$\\3")
)
```

# learned

- `defun` and interactive
- escape `\` into `\\`
- `(` and `{` needs to be espcated if for symantic use
- `\1`, `\2` to refer to the captured content