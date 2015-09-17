#Grunt Task for Swagger JS Codegen

[![Build Status](http://img.shields.io/travis/wcandillon/grunt-swagger-js-codegen/master.svg?style=flat)](https://travis-ci.org/wcandillon/grunt-swagger-js-codegen) [![NPM version](http://img.shields.io/npm/v/grunt-swagger-js-codegen.svg?style=flat)](http://badge.fury.io/js/grunt-swagger-js-codegen) [![Code Climate](http://img.shields.io/codeclimate/github/wcandillon/grunt-swagger-js-codegen.svg?style=flat)](https://codeclimate.com/github/wcandillon/grunt-swagger-js-codegen)

##Examples
###Nodejs generation
[See example.](https://github.com/28msec/28.io-nodejs/blob/master/Gruntfile.js#L11)
```javascript
    grunt.initConfig({
        'swagger-js-codegen': {
            queries: {
                options: {
                    apis: [
                        {
                            swagger: 'swagger/_queries',
                            moduleName: 'Model' // This is the model and file name
                        }
                    ],
                    dest: 'lib'
                },
                dist: {
                }
            }
        }
    });
```

###Angularjs generation
[See example.](https://github.com/28msec/28.io-angularjs/blob/master/Gruntfile.js#L27)
```javascript
    grunt.initConfig({
        'swagger-js-codegen': {
            queries: {
                options: {
                    apis: [
                        {
                            swagger: 'swagger/_queries',
                            moduleName: 'Model', // This is the model and file name
                            angularjs: true
                        }
                    ],
                    dest: 'lib'
                },
                dist: {
                }
            }
        }
    });
```

###Custom generation
```javascript
    grunt.initConfig({
        'swagger-js-codegen': {
            queries: {
                options: {
                    apis: [
                        {
                            swagger: 'swagger/_queries',
                            moduleName: 'Model' // This is the file name
                            mustache: {
                                moduleName: 'Model' // This is the model name - it should be repeated here if you want to use it in mustache templates
                                customParam: 'foo'  //some custom param used in mustache templates
                            },
                            template: {
                              class: fs.readFileSync('custom-angular-class.mustache', 'utf-8'),
                              method: fs.readFileSync('custom-method.mustache', 'utf-8'),
                              request: fs.readFileSync('custom-angular-request.mustache', 'utf-8')
                            },
                            custom : true
                        }
                    ],
                    dest: 'lib'
                },
                dist: {
                }
            }
        }
    });