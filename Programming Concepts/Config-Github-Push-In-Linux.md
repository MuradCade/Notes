normally when we push project to github using git if the project is cloned over https you should create file in the  ~ directory , file name should be  .netrc , when you create file put inside of it the following content as its.

```vim
    machine github.com
        login <your username>
        password <your token>
```

now you are all set , you can push what ever you want.