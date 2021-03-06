#+BEGIN_HTML
<a href="https://elpa.gnu.org/packages/dired-git-info.html"><img alt="GNU ELPA" src="https://elpa.gnu.org/favicon.png"/></a>
#+END_HTML

* Description

This Emacs packages provides a minor mode which shows git information inside
the dired buffer:

[[./images/screenshot2.png]]

* Installation

** GNU ELPA

This package is available on [[https://elpa.gnu.org][GNU ELPA]]. You can install it via =M-x package-install RET dired-git-info RET=

** Manual

For manual installation, clone the repository and call:

#+BEGIN_SRC elisp
(package-install-file "/path/to/dired-git-info.el")
#+END_SRC

* Config

** Bind the minor mode command in dired

#+BEGIN_SRC elisp
(with-eval-after-load 'dired
  (define-key dired-mode-map ")" 'dired-git-info-mode))
#+END_SRC

** Don't hide normal Dired file info

By default, toggling =dired-git-info-mode= also toggles the built-in
=dired-hide-details-mode=, which hides file details such as ownership,
permissions and size. This behaviour can be disabled by overriding
=dgi-auto-hide-details-p=:

#+BEGIN_SRC elisp
(setq dgi-auto-hide-details-p nil)
#+END_SRC

** Enable automatically in every Dired buffer (if in Git repository)

To enable =dired-git-info-mode= whenever you navigate to a Git repository, use
the following (if you want to use this you have to install from source as long
this change is not picked up by ELPA):
#+BEGIN_SRC elisp
(add-hook 'dired-after-readin-hook 'dired-git-info-auto-enable)
#+END_SRC

