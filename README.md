# persoo-templates
==========
Templates for Persoo widgets



## Installation

  `npm install persoo-templates`

## Usage

    var persooTemplates = require('persoo-templates');
    
    var offerTemplate = {
        "class": "webWidget",
        "name": "Custom HTML",
        "fields": [
            {
                "id": "fieldID",
                "label": "My field",
                "formFieldType": "html",
                "defaultValue": "<div>...your html code with EJS...</div>"
            }
        ],
        "template": "Master template using predefined field as EJS variables, i.e. <%= fieldID %>",
        "minScenariosCount": 0
    };
    var offer = {
    		variants: [{
    			templateID: 'templateID1',
    			content: {
    			    fieldID: 'myFieldValue'
    			},
    			scenarios: [
    			    {id: 'products1', scenarioID: 'sampleScenarioID'}
    			]
    		}]
    };
    var context = {};
        
    var renderedHTML = persooTemplates.render(offerTemplate, offer.variants[0], context);
  
  Output should be `Master template using predefined field as EJS variables, i.e. myFieldValue`
  
  See unit tests for more examples.


## Tests

  `npm test`

## Editor
  
  For easy templates debuging and unit testing, you can use JSON editor with widget preview.
  Run `npm run build` and then open /editor/preview.html in your browser.
  
  Chrome does not allow to load JSON file with templates through file:// protocol. Thus if you cannot access preview.html 
  through http:// protocol (from local webserver), try to start Chrome with allowed access to local files
  (generally it is not permitted because of security reasons).
  
  On Windows:
  
	chrome.exe --allow-file-access-from-files
	
  On Mac:

	open /Applications/Google\ Chrome.app/ --args --allow-file-access-from-files

## Contributing

In lieu of a formal style guide, take care to maintain the existing coding style. Add unit tests for any new or changed functionality. Lint and test your code.
