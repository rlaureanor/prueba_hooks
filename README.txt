This pen is used only for teaching purposes and i'm not the owner of it.

All kudos for steroyle.

A Pen created at CodePen.io. You can find this one at http://codepen.io/steroyle/pen/LNzyzP.


# Pre-requisites

Install [stylelint](https://github.com/stylelint/stylelint) on your computer.

Fork this repo (For the sake of being able to send commits to the remote repo), and clone it in your local machine.

Type this commands in your terminal

```bash
cd prueba_hooks
cd .git/hooks
touch pre-commit
chmod 744 pre-commit
```

Edit **pre-commit** file with the following content and save it:


```bash
#!/bin/sh
stylelint --config ${PWD}/stylelint-conf.json ${PWD}/css/*.css
if [[ "$?" == 0 ]]; then
   echo "Looks good!"
   exit 0
else
   echo "Review your css. Aborting..."
   exit 1
fi
```

Edit [style.css](https://github.com/ntkog/prueba_hooks/blob/master/css/style.css) , add the file to the staging area , and try to do a commit

Probably you will see this message:

```bash
css/style.css
 21:11  ✖  Unexpected unit "px"   unit-whitelist
 22:12  ✖  Unexpected unit "px"   unit-whitelist
 27:11  ✖  Unexpected unit "px"   unit-whitelist
 28:14  ✖  Unexpected unit "px"   unit-whitelist
 39:12  ✖  Unexpected unit "px"   unit-whitelist
 39:16  ✖  Unexpected unit "px"   unit-whitelist
 40:11  ✖  Unexpected unit "px"   unit-whitelist
 49:12  ✖  Unexpected unit "px"   unit-whitelist
 54:12  ✖  Unexpected unit "px"   unit-whitelist
 54:17  ✖  Unexpected unit "px"   unit-whitelist
 54:22  ✖  Unexpected unit "px"   unit-whitelist

Review your css. Aborting...

```

Review the file [stylelint-conf.json](https://github.com/ntkog/prueba_hooks/blob/master/stylelint-conf.json) , to see which rules applied,
and modify it to make it pass.
