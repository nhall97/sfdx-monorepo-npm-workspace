# sfdx-monorepo-workspace
sfdx monorepo using NPM Workspaces to work with multiple sfdx projects eg. packages

The project is structured in the following
```
packages/
    /sfdx-core-package
        /package.json
    /sfdx-bonus-package
        /package.json
 package.json'
 ```
 
This is to provide a monorepo structure to our sfdx packages. The idea being that you can clone one repo, and work across many packages - to help make dependency management easier as well as refactoring.


The goal is to be able to provide a template sfdx-monorepo-workspace - to allow people to follow the same pattern with ease.

## Instructions
//Check prereqs below before starting (npm > 7.0)
'git clone <repo>'
'npm install'

test out below workspace commands that you're familiar with with sfdx:
'npm lint'  : run linting across core package, and bonus package
  
## ToDo
<ol>
  <li> Create workspace                           -Completed-
  <li> Create a first package                     -Completed-
  <li> Create a second package                    -Completed-
  <li> Link packages to Workspace                 -Completed-
  <li> Run npm install to generate package-lock   -Completed-
  <li> Validate sfdx commands in workspace
</ol>

# Outcomes
 Are there any advantages to developing packages in a workspace?

## SFDX Command Validations
| SFDX Command                                                                                                               | Workspace Command            | Working? |
|----------------------------------------------------------------------------------------------------------------------------|------------------------------|----------|
| "lint": "npm run lint:lwc && npm run lint:aura",                                                                           | npm run lint --ws            |     N    |
| "lint:aura": "eslint **/aura/**",                                                                                          |                              |          |
| "lint:lwc": "eslint **/lwc/**",                                                                                            |                              |          |
| "test": "npm run test:unit",                                                                                               |                              |          |
| "test:unit": "sfdx-lwc-jest",                                                                                              |                              |          |
| "test:unit:watch": "sfdx-lwc-jest --watch",                                                                                |                              |          |
| "test:unit:debug": "sfdx-lwc-jest --debug",                                                                                |                              |          |
| "test:unit:coverage": "sfdx-lwc-jest --coverage",                                                                          |                              |          |
| "prettier": "prettier --write \"**/*.{cls,cmp,component,css,html,js,json,md,page,trigger,xml,yaml,yml}\"",                 | npm run prettier --ws        |     Y    |
| "prettier:verify": "prettier --list-different \"**/*.{cls,cmp,component,css,html,js,json,md,page,trigger,xml,yaml,yml}\"", | npm run prettier:verify --ws |     Y    |
| "precommit": "lint-staged",                                                                                                | npm run precommit --ws       |     Y    |
| "prepare": "cd ../../ && husky install front/.husky"                                                                       | npm run prepare --ws         |     N    |
  
## PreReqs
<li> npm 7.0 >
<lI> husky > v7.0.1 due to this https://github.com/typicode/husky/issues/1003#issuecomment-874667232

## Lessons Learned
<li> Husky should be installed in monorepo root - seems to fix issues with installs only in packages
