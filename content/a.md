---
title: ""
date: 2020-10-21T20:55:18+02:00
draft: true
---

# Software Quality Assurance

---

#### Testing

In this project we used “Mocha” JavaScript test framework which is running on Node. js and “Chai” which is a BDD / TDD assertion library.

First we created folder in the project for testing.
In the command line:

     mkdir test

In order to create new test we need to install npm packages:

     npm init

Than we install mocha and chai:

     npm install chai --save-dev

And change the directory to the test folder:

     cd test

We create a new file appTest.js – here we will conduct our tests.
In order to use functions we export them from app.js file.

     module.exports = {
         get_tasks,
         add_task,
         update_task,
         delete_task,
         tasks,
         new_task
      };

In appTest.js file in order to use our libraries we need to add them:

     const assert = require('chai').assert;
     const expect = require('chai').expect;
     const app = require('../app');

In order to create a test we use:

     describe('Test Name', function() {
        it("check if variable 'tasks' is an array ofobjects"
     function() {
        assert.isArray(tasks);
       })
     })

To run the test we type “npm test” in the command line, than we can see the test results in the console:

     Test Name
          √ check if variable 'tasks' is an array of objects
          √ check if 'tasks' array contains all the expected objects
          √ check if function get_tasks return array of tasks correctly
          √ check if new_tasks object contains properties 'id' and 'description'
     4 passing (11ms)

---

# Integrated Development Environment (VIM)

---

###### Setup instructions:

Since we’re working with JavaScript, we are using the two following plugins:

- vim-javascript for the syntax highlight
- ALE for integrated lintinVimg

In order to get the setup right, first follow the installation guide for vim-javascript:

Open your terminal and paste the following code:

      git clone https://github.com/pangloss/vim-javascript.git
     ~/.vim/pack/vim-javascript/start/vim-javascript

After the installation is finished, open the .vimrc file on your computer and paste there a following line:

     let g:javascript_plugin_jsdoc = 1

This will enable the syntax highlighting in vim on your device.
In order to ensure, whether the installation worked, open the project file (type vim app.js in the CLI in the project root) and check, whether all the “return” statements are highlighted in orange/brown color.

Next, proceed to the linter installation.

1.Open the terminal and paste the following code:

     git clone --depth 1 https://github.com/dense-analysis/ale.git
     ~/.vim/pack/git-plugins/start/ale

2.After the installation is finished, open the .vimrc file on your device and paste the following lines:

     let g:ale_linters = {'javascript': ['eslint']}
     packloadall

Before you proceed to the next part, make sure this part worked. Open the file (type vim app.js in the CLI from the project root), press “ESC” and type the following:

     :ALEInfo

You should see the list of presets similar to what you have just pasted into your .vimrc file. If you can see the list, it means the first part of the installation was successful.

3.Exit the file without saving (press ESC and type :q!) and within the project root, type:

     npm install eslint

After the download is finished, create a file with eslint configuration. You can do it directly from CLI. In the root of the project type:

     vim .eslintrc.js

Vim will create a new, empty file for you, in which you should paste following:

     module.exports = {
         "env": {
             "browser": true,
             "es2021": true
         },
         "extends": "eslint:recommended",
         "parserOptions": {
             "ecmaVersion": 12,
             "sourceType": "module"
         },
         "rules": {
         }
      };

After you are done, press ESC and type :x in order to exit the file while keeping the changes.

4.To check whether the integration with the linter worked, open the project file again (vim app.js). Try making a mistake somewhere in the file and wait for the red highlights of the errors. If you do not see the errors highlighted, but you have passed successfully through all of the previous parts, it might mean that you need to upgrade your vim to vim 8.
