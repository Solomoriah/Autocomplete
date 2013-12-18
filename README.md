Autocomplete
============

Ajax Autocomplete for Prototype
Copyright 2010 Tomas Kirda

Revised edition Copyright 2013 Chris Gonnerman

See the LICENSE file for license details.

About this Module
=================

This is a revised version of Tomas Kirda's original Autocomplete for Prototype.
He has ceased maintaining it, and so I have forked this version.

The documentation below is taken from Tomas' website, and revised to reflect
the current version.

Installation
============

Include Prototype 1.7.x in your header, and following that, include the
autocomplete script.

    <script type="text/javascript" src="prototype.js"></script>
    <script type="text/javascript" src="autocomplete.js"></script>

Usage
=====

Here is an Ajax Autocomplete sample for the text field with id "query"

    <input type="text" name="q" id="query">

Create an instance of the Autocomplete object. You can have multiple instances on a single page.

    <script type="text/javascript">
    new Autocomplete('query', { serviceUrl:'service/autocomplete.ashx' });
    </script>

You can add extra options:

    new Autocomplete('query', {
        serviceUrl:'service/autocomplete.ashx',
        minChars:2,
        maxHeight:400,
        width:300,
        deferRequestBy:100,
        // callback function:
        onSelect: function(value, data){
            alert('You selected: ' + value + ', ' + data);
        }
    });

Web page that provides data for Ajax Autocomplete, in our case
autocomplete.ashx will receive GET request with querystring ?query=Li, and it
must return JSON data in the following format:

    {
        query: 'Li',
        suggestions: ['Liberia','Libyan Arab Jamahiriya','Liechtenstein','Lithuania'],
        data: ['LR','LY','LI','LT']
    }

Notes:

> query - original query value
> suggestions - comma separated array of suggested values
> data (optional) - data array, that contains values for callback function when data is selected.

