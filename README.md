** ESLint Configuration settings for projects in VS Studio Code
https://code.visualstudio.com/docs/nodejs/reactjs-tutorial


First, install the ESLint command line tool:

    npm install -g eslint
Then install the ESLint extension by going to the Extensions view and typing 'eslint'.

ESLint extension

Once the ESLint extension is installed and VS Code reloaded, you'll want to create an ESLint configuration file .eslintrc.json. You can create one using the extension's ESLint: Create ESLint configuration command from the Command Palette (⇧⌘P).

    create eslintrc

The command will create a .eslintrc.json file in your project root:

    {
    "env": {
        "browser": true,
        "commonjs": true,
        "es6": true,
        "node": true
    },
    "parserOptions": {
        "ecmaFeatures": {
            "jsx": true
        },
        "sourceType": "module"
    },
    "rules": {
        "no-const-assign": "warn",
        "no-this-before-super": "warn",
        "no-undef": "warn",
        "no-unreachable": "warn",
        "no-unused-vars": "warn",
        "constructor-super": "warn",
        "valid-typeof": "warn"
    }
    }
ESLint will now analyze open files and shows a warning in index.js about 'App' being defined but never used.

App is unused

You can modify the ESLint rules and the ESLint extension provides IntelliSense in .eslintrc.json.

eslintrc IntelliSense

Let's add an error rule for extra semi-colons:

    "rules": {
        "no-const-assign": "warn",
        "no-this-before-super": "warn",
        "no-undef": "warn",
        "no-unreachable": "warn",
        "no-unused-vars": "warn",
        "constructor-super": "warn",
        "valid-typeof": "warn",
        "no-extra-semi":"error"
    }
Now when you mistakenly have multiple semicolons on a line, you'll see an error (red squiggle) in the editor and error entry in the Problems panel.

extra semicolon error

## EditorConfig override settings

Editing an EditorConfig file
EditorConfig files use a straightforward file layout to specify settings, which is explained below using a previous example:

EditorConfig:


    # This file is the top-most EditorConfig file
    root = true

    # All Files
    [*]
    indent_style = space
    indent_size = 4
    insert_final_newline = false
    trim_trailing_whitespace = false

    [*.cs]
    csharp_new_line_before_open_brace = none


Setting root to true flags this file as the top-most file of the codebase and any higher .editorconfig files in the project are ignored, as explained in the Override EditorConfig Settings section.

Each section is denoted by square ([ ]) braces and specifies information on the types of files the following properties should pertain to.

In the example above, some settings are applied to all files in the project and others are added only to C# files. The screenshots below show before and after the .editorconfig settings have been applied: