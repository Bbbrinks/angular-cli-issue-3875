Reproduction of: https://github.com/angular/angular-cli/issues/3875
When creating a component in a lib project and using npm link an error occurs on ng build.
This is because angular-cli/webpack looks for classes in the /frontend/node_modules/@test/lib/node_modules directory

* npm install (both subdirs)
* npm link (in ./lib)
* npm link @test/lib (in frontend)
* ng build

Results in:
ERROR in Error encountered resolving symbol values statically. Calling function 'makeDecorator', function calls are not supported. Consider replacing the function or lambda with a reference to an exported function, resolving symbol NgModule in /test/frontend/node_modules/@test/lib/node_modules/@angular/core/src/metadata/ng_module.d.ts, resolving symbol NgModule in /test/frontend/node_modules/@test/lib/node_modules/@angular/core/src/metadata.d.ts, resolving symbol NgModule in /test/frontend/node_modules/@test/lib/node_modules/@angular/core/src/core.d.ts, resolving symbol NgModule in /test/frontend/node_modules/@test/lib/node_modules/@angular/core/index.d.ts, resolving symbol TestModule in /test/frontend/node_modules/@test/lib/src/test.module.ts, resolving symbol TestModule in /test/frontend/node_modules/@test/lib/src/test.module.ts
