# Sample JS ES5 Class

```javascript
'use strict';

var fs = require('fs');
var util = require("util");
var events = require("events");

//any object extend library
var extend = require('extend'); 

/**
 * Creates a new Person.
 * @param {string} var1 Description of a parameter
 * @param {Object[]} [var2] Array of Objects. Brackets means, it's optional
 * @class
 */
function Classname (var1, var2) {
    this.publicProperty = var1;

    if (var2 === null) {
        this._privateProperty = true;
    }
}

// inherits always after constructor
util.inherits(Classname, events.EventEmitter);

// we dont like this syntax: Classname.prototype.publicMethod = function() {
var prototype = {

    CONSTANT_1: 1,
    CONSTANT_2: 2,

    /**
     *  It's good to keep enumerations together 
     */
    ENUM_A: 1,
    ENUM_B: 2,

    /**
     * @type {string} It's good to describe public properties
     */
    publicProperty: null,

    _privateProperty: false,

    /**
     * We should keep public methods commented
     *
     * @param {boolean} someArg
     * @returns {number}
     */
    publicMethod: function (someArg) {
        // descriptive IF's are better!
        var argIsValid = typeof someArg === 'string'
            && someArg.match(/^K/);

        if (argIsValid) {
            return 12;
        }

        return 10;
    },

    /**
     * Sometimes we should comment private methods too.
     * It's good to keep one line space there.
     *
     * @param {boolean} someArg
     * @private
     */
    _privateMethod: function (path, bar)
    {
        fs.stat(path, this._callbackFactory(bar));
    },

    _callbackFactory: function (bar)
    {
        var self = this;
        return function someCallback (err, res) {
            console.log(res, bar, self._privateProperty);
        };
    }
};

extend(Classname.prototype, prototype);

module.exports = Classname;

```

# Sample service

```javascript
'use strict';

var Classname = require('./Classname');
var cfg = require('../../config');
var fs = require('fs');

var service = {

    /* A CACHED VALUE */
    _cachedSomething: null,

    _initialize: function () {
        // private initialization
    },

    /**
     * We should keep public methods commented
     *
     * @param {boolean} someArg
     * @returns {Classname}
     */
    aSampleFactory: function (someArg) {
        
        var ret = new Classname(someArg);

        return ret;
    },

    /**
     * We should keep public methods commented
     *
     * @param {function} callback
     */
    getSomethingLazily: function (callback) {
        if (this._cachedSomething === null) {
            var self = this;
            fs.stat('somefile.txt', function loadSomeFile (err, res) {

                // deep: 4 levels max 
                if (err === null) {
                    self._cachedSomething = res;
                    callback(null, res);
                } else {
                    callback(err, null);
                }
            });
        } else {
            callback(null, this._cachedSomething);
        }
    }

};

service._initialize();

module.exports = service;

```