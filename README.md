# accounts-ui-bootstrap-3-angular
AngularJS wrapper for
[ian:accounts-ui-bootstrap-3](https://github.com/ianmartorell/meteor-accounts-ui-bootstrap-3)
package. You can get full instructions about how to use the package
there.

# How to install
1. Make sure you have the `angular` package installed.

2. Add the package:
`meteor add carlosbaraza:accounts-ui-bootstrap-3-angular`

3. Add a dependency on your AngularJS module. For example:
```javascript
angular.module('myApp', ['angular-meteor', 'accounts.ui']);
```

# How to use
Use it in your app, for example:
```html
<login-buttons></login-buttons>
```

A full example might be:
```html
<div class="navbar navbar-default" role="navigation">
  <div class="navbar-header">
    <a class="navbar-brand" href="#">Project name</a>
    <button type="button" class="navbar-toggle collapsed" data-toggle="collapse" data-target=".navbar-collapse">
      <span class="sr-only">Toggle navigation</span>
      <span class="icon-bar"></span>
      <span class="icon-bar"></span>
      <span class="icon-bar"></span>
    </button>
  </div>
  <div class="navbar-collapse collapse">
    <ul class="nav navbar-nav">
      <li class="active"><a href="#">Link</a></li>
    </ul>
    <ul class="nav navbar-nav navbar-right">
      <login-buttons></login-buttons>
    </ul>
  </div>
</div>
```

# Custom templates
In order to set custom templates, we have to create a package called
`accounts-ui-bootstrap-3-angular-templates` like this:
```
meteor create --package accounts-ui-bootstrap-3-angular-templates
```

Then we should delete all the content of the folder
`packages/accounts-ui-bootstrap-3-angular-templates` and replace the content of
`package.js` with this:
```javascript
Package.describe({
  name: 'accounts-ui-bootstrap-3-angular-templates',
  version: '0.0.1'
});

Package.onUse(function(api) {
  api.versionsFrom('1.2.1');
  api.use('blaze-html-templates');

  api.addFiles('custom-templates.html');
});
```

As you can see we use 'blaze-html-templates' to have the ability of
setting up the custom templates as it is said in the official docs
([ian:accounts-ui-bootstrap-3](https://github.com/ianmartorell/meteor-accounts-ui-bootstrap-3)).

Then we create a file called `custom-templates.html` and there we
can write down our custom templates:
```html
<template name="_loginButtonsAdditionalLoggedInDropdownActions">
  <a class="btn btn-success btn-block" id="login-buttons-members"
     href="/members/requests">
    <span class="glyphicon glyphicon-th" aria-hidden="true"></span> Espace membre
  </a>
</template>
```

Finally, do not forget to add your package to the project:
```
meteor add accounts-ui-bootstrap-3-angular-templates
```

# Localization and other configuration
This kind of configuration should be done in the client, and it is not affected
by the fact of using `angular`, so the official docs from the package should be
used. ([ian:accounts-ui-bootstrap-3](https://github.com/ianmartorell/meteor-accounts-ui-bootstrap-3))
