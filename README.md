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

Styling
=======

Script generates the following HTML (sample query Li). Active element when you
navigate up and down is marked with class "selected". You can style it any way
you wish.

    <div class="autocomplete-w1">
      <div style="width:299px;" id="Autocomplete_1240430421731" class="autocomplete">
        <div><strong>Li</strong>beria</div>
        <div><strong>Li</strong>byan Arab Jamahiriya</div>
        <div><strong>Li</strong>echtenstein</div>
        <div class="selected"><strong>Li</strong>thuania</div>
      </div>
    </div>

Here is style used in the sample above:

    .autocomplete-w1 {
      background:url(img/shadow.png) no-repeat bottom right;
      position:absolute;
      top:4px;
      left:3px;
      /* IE6 fix: */ _background:none;
      _top:1px;
    }

    .autocomplete {
      width:300px;
      border:1px solid #999;
      background:#FFF;
      cursor:default;
      text-align:left;
      max-height:350px;
      overflow:auto;
      margin:-6px 6px 6px -6px;
      /* IE specific: */ _height:350px;
      _margin:0px 6px 6px 0;
      overflow-x:hidden;
    }

    .autocomplete .selected {
      background:#F0F0F0;
    }

    .autocomplete div {
      padding:2px 5px;
      white-space:nowrap;
    }

    .autocomplete strong {
      font-weight:normal;
      color:#3399FF;
    }

If you will use this CSS, please make sure to correct path to the shadow.png
image. Image is included in the package. It uses CSS Drop Shadow technique by
Sergio Villarreal.

