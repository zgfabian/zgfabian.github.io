---
title: "Dired, the default file manager in Emacs "
categories: emacs
tags: dired
language: en
layout: post
---

`Dired (C-x d)` is a file manager in Emacs. My setup has the following features: dual-panes withd dwim (do what I mean), hide/show file attributes, display/hide dot files, all-the-icons theme.

* Dual-panes and interactions ([dwim](https://en.wikipedia.org/wiki/DWIM) copy, move) between the panes.

I am using a convenience elisp function (`(dual-dired)`) binded to `C-c d` combo[^1].

```elisp
      (defun dual-dired ()
      "Open 2 dired buffers side by side."
      (interactive)
      (let ((original-window (selected-window)))
        (dired ".") ;; current directory
        (split-window-right)
        (other-window 1)
        (dired ".")
        (select-window original-window)))
    ;; Bind the function to a key combination
    (keymap-global-set "C-c d" 'dual-dired)
```

* Hide/show file properties (`M-x dired-hide-details-mode`)

{: .box-warning :}
By pressing `(` key, which is the default .

* Hide/show dotfiles

{: .box-warning :}
Using a custom `C-.` binding.

```emacs-lisp
      (setq dired-omit-files "^\\...+$")
      (global-set-key (kbd "C-.") 'dired-omit-mode)
```

* Icons with all-the-icons

{: .box-warning :}
Installed `all-the-icons-dired` package.

```emacs-lisp
      (use-package all-the-icons-dired
        ;; :ensure t
        :config
        (setq all-the-icons-scale-factor 1)
        (setq all-the-icons-dired-monochrome nil)
        :hook
        (dired-mode . all-the-icons-dired-mode)
        )
```
[![See screenshot here.]({{ site.baseurl }}/assets/img/25-11-01-emacs-dired/emacs-dired.png)]({{ site.baseurl }}/assets/img/25-11-01-emacs-dired/emacs-dired.png)

* Excerpt from `init.el`:

```emacs-lisp
      (use-package dired
        :config
        ;; stop proliferating buffers
        (setq dired-kill-when-opening-new-dired-buffer t)
        ;; default target other window for file operations (copy, move)
        (setq dired-dwim-target t)
        ;; confirm recursive deletion or copy
        ;; 'top means ask every time
        ;; 'always means no asking
        (setq dired-recursive-copies 'top)
        (setq dired-recursive-deletes 'top)
        :hook
        (dired-mode . dired-hide-details-mode) ;;
        (dired.mode . dired-omit-mode) ;; hide dotfiles, etc
        )
```
<br>

[^1]: `C-c d` means hold the `CONTROL` key while typing the character `c`. *Release* it, then press character `d` on your keyboard.
