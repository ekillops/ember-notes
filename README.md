# Ember Notes

[windows only] `> ember-cli-windows`

----------------------------------

`>ember new [project-name]`

----------------------------------

`>ember install ember-bootstrap`

----------------------------------
 
`>ember install ember-cli-sass`

  _change name of app.css file to app.scss_

----------------------------------

`>ember install emberfire`
  
  _create .json file and import to firebase project to seed database_
  
  _configure firebase in config/environment.js ->_
	
	`var ENV = { 
		...
		...
	 	firebase: {
    		  	apiKey: 'xyz',
    		  	authDomain: 'YOUR-FIREBASE-APP.firebaseapp.com',
   	 	  	databaseURL: 'https://YOUR-FIREBASE-APP.firebaseapp.com',
    		  	storageBucket: 'YOUR-FIREBASE-APP.appspot.com',
  		  	},
		}`

----------------------------------

`>ember g[enerate] model [model-name]`

  _fill in model details matching .json and firebase properties exactly ->_

	`export default DS.Model.extend({
  		propertyOne: DS.attr(),
  		propertyTwo: DS.attr(),
  		propertyThree: DS.attr()
		});`

  _relationships are estabilished in models ->_

	models/rental.js ->
 
		`export default DS.Model.extend({
		  DS.hasMany('review', { async: true })
		});`

	models/review.js ->

		`export default DS.Model.extend({
  		  rental: DS.belongsTo('rental', { async: true })
		});`

  _return multiple models with and rsvp hash ->_
  
    `model() {
        return Ember.RSVP.hash({
        rentals: this.store.findAll('rental'),
        reviews: this.store.findAll('review')
      });
    },`

----------------------------------

`>ember g route index`

  _index must be generated manually but does not require and entry in router.js_

----------------------------------

`>ember g route [route-name]`

	_dynamic route configure in router.js ->_
	 
	`this.route('route', {path: '/route/:route_param'});`

----------------------------------

`>ember g component [component-name]`

----------------------------------

`>ember g template application`

  _use application template as an overall layout for your site with header/footer/nav etc._

  _application.hbs should contain at least an {{outlet}} tag, where other templates will be displayed_

----------------------------------

`>ember s[erve]`

----------------------------------

Additional Notes:

- When using `this.get('input_field')` to gather form input, helper MUST have value attribute, and written without quotes -> `{{input value=fieldName}}`

- Never trust `this`
