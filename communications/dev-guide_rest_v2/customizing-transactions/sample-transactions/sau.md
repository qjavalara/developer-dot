---
layout: page
title: Chapter 4.3.8 - Sales and Use
product: communications
doctype: comms_rest_v2_dev_guide
chapter: customizing-transactions
nav: apis
disqus: 0
---

<ul class="pager">
  <li class="previous"><a href="/communications/dev-guide_rest_v2/customizing-transactions/sample-transactions/safe-harbor-override/"><i class="glyphicon glyphicon-chevron-left"></i>Previous</a></li>
  <li class="next"><a href="/communications/dev-guide_rest_v2/customizing-transactions/sample-transactions/private-line/">Next<i class="glyphicon glyphicon-chevron-right"></i></a></li>
</ul>

REST v2 provides Sales and Use taxes in addition to Communications taxes.

<h3>Sales and Use Example</h3>
Sales and Use Transaction/Service Pairs (<code>tran</code> and <code>serv</code>) are used.  To find a list of Sales and Use Transaction/Service Pairs, use the <code>/api/v2/afc/tspairs</code> <a class="dev-guide-link" href="/communications/dev-guide_rest_v2/getting-started/environments-endpoints/">endpoint</a>.

{% highlight json %}
{
  "cmpn": {
    "bscl": 0,
    "svcl": 0,
    "fclt": false,
    "frch": false,
    "reg": false
  },
  "inv": [
    {
      "doc": "TEST-SAU INVOICE 2018.05.01:12.02 AVA",
      "cmmt": false,
      "bill": {
        "cnty": "San Francisco",
        "ctry": "USA",
        "int": true,
        "geo": false,
        "city": "San Francisco",
        "st": "CA",
        "zip": "94102"
      },
      "cust": 0,
      "lfln": false,
      "date": "2018-05-01T12:00:00Z",
      "itms": [
        {
          "ref": "Line Item 001 - Retail Sale General Merchandise/General Rule Default Attribute-Property",
          "chg": 100,
          "line": 0,
          "sale": 1,
          "incl": false,
          "tran": 34,
          "serv": 106,
          "prop": 0,
          "dbt": false,
          "adj": false
        },
        {
          "ref": "Line Item 002 - Consumer Use General Merchandise/General Rule Discount Attribute-Cash Discount Property",
          "chg": 100,
          "line": 0,
          "sale": 2,
          "incl": false,
          "tran": 34,
          "serv": 106,
          "prop": 13,
          "dbt": false,
          "adj": false
        },
        {
          "ref": "Line Item 003 - Vendor Use General Merchandise/General Rule Discount Attribute-Coupons Third Party Property",
          "chg": 100,
          "line": 0,
          "sale": 3,
          "incl": false,
          "tran": 34,
          "serv": 106,
          "prop": 7,
          "dbt": false,
          "adj": false
        }
      ],
      "invm": true,
      "dtl": true,
      "summ": true,
      "opt": [
        {
          "key": "1",
          "val": "SAU Sample Line Items Invoice ABC-ZZZ"
        }
      ]
    }
  ]
}
{% endhighlight %}

<h4>Response</h4>
Sales and Use taxes, identified by the <b>SALES AND USE TAXES</b> category (<code>cat</code>), are returned.

<div class="panel-group">
  <a data-toggle="collapse" href="#collapse1">View the Response JSON</a>
  <div id="collapse1" class="panel-collapse collapse">
    <div class="panel-body">
{% highlight json %}
{
  "inv": [
    {
      "doc": "TEST-SAU INVOICE 2018.05.01:12.02 AVA",
      "itms": [
        {
          "ref": "Line Item 001 - Retail Sale General Merchandise/General Rule Default Attribute-Property",
          "txs": [
            {
              "bill": true,
              "cmpl": true,
              "tm": 100,
              "calc": 1,
              "cat": "SALES AND USE TAXES",
              "cid": 1,
              "name": "District Tax",
              "exm": 0,
              "lns": 0,
              "min": 0,
              "pcd": 377200,
              "rate": 0.0125,
              "sur": false,
              "tax": 1.25,
              "lvl": 2,
              "tid": 4
            },
            {
              "bill": true,
              "cmpl": true,
              "tm": 100,
              "calc": 1,
              "cat": "SALES AND USE TAXES",
              "cid": 1,
              "name": "Sales Tax",
              "exm": 0,
              "lns": 0,
              "min": 0,
              "pcd": 377300,
              "rate": 0.0125,
              "sur": false,
              "tax": 1.25,
              "lvl": 2,
              "tid": 1
            },
            {
              "bill": true,
              "cmpl": true,
              "tm": 100,
              "calc": 1,
              "cat": "SALES AND USE TAXES",
              "cid": 1,
              "name": "Sales Tax",
              "exm": 0,
              "lns": 0,
              "min": 0,
              "pcd": 377300,
              "rate": 0.06,
              "sur": false,
              "tax": 6,
              "lvl": 1,
              "tid": 1
            }
          ]
        },
        {
          "ref": "Line Item 002 - Consumer Use General Merchandise/General Rule Discount Attribute-Cash Discount Property",
          "txs": [
            {
              "bill": true,
              "cmpl": true,
              "tm": 100,
              "calc": 1,
              "cat": "SALES AND USE TAXES",
              "cid": 1,
              "name": "Consumer Use Tax",
              "exm": 0,
              "lns": 0,
              "min": 0,
              "pcd": 377300,
              "rate": 0.0125,
              "sur": false,
              "tax": 1.25,
              "lvl": 2,
              "tid": 357
            },
            {
              "bill": true,
              "cmpl": true,
              "tm": 100,
              "calc": 1,
              "cat": "SALES AND USE TAXES",
              "cid": 1,
              "name": "Consumer Use Tax",
              "exm": 0,
              "lns": 0,
              "min": 0,
              "pcd": 377300,
              "rate": 0.06,
              "sur": false,
              "tax": 6,
              "lvl": 1,
              "tid": 357
            },
            {
              "bill": true,
              "cmpl": true,
              "tm": 100,
              "calc": 1,
              "cat": "SALES AND USE TAXES",
              "cid": 1,
              "name": "District Consumer Use Tax",
              "exm": 0,
              "lns": 0,
              "min": 0,
              "pcd": 377200,
              "rate": 0.0125,
              "sur": false,
              "tax": 1.25,
              "lvl": 2,
              "tid": 358
            }
          ]
        },
        {
          "ref": "Line Item 003 - Vendor Use General Merchandise/General Rule Discount Attribute-Coupons Third Party Property"
        }
      ],
      "summ": [
        {
          "max": 2147483647,
          "min": 0,
          "tchg": 100,
          "calc": 1,
          "cat": "SALES AND USE TAXES",
          "cid": 1,
          "name": "District Tax",
          "exm": 0,
          "lns": 0,
          "pcd": 377200,
          "rate": 0.0125,
          "sur": false,
          "tax": 1.25,
          "lvl": 2,
          "tid": 4
        },
        {
          "max": 2147483647,
          "min": 0,
          "tchg": 100,
          "calc": 1,
          "cat": "SALES AND USE TAXES",
          "cid": 1,
          "name": "Sales Tax",
          "exm": 0,
          "lns": 0,
          "pcd": 377300,
          "rate": 0.0125,
          "sur": false,
          "tax": 1.25,
          "lvl": 2,
          "tid": 1
        },
        {
          "max": 2147483647,
          "min": 0,
          "tchg": 100,
          "calc": 1,
          "cat": "SALES AND USE TAXES",
          "cid": 1,
          "name": "Sales Tax",
          "exm": 0,
          "lns": 0,
          "pcd": 377300,
          "rate": 0.06,
          "sur": false,
          "tax": 6,
          "lvl": 1,
          "tid": 1
        },
        {
          "max": 2147483647,
          "min": 0,
          "tchg": 100,
          "calc": 1,
          "cat": "SALES AND USE TAXES",
          "cid": 1,
          "name": "Consumer Use Tax",
          "exm": 0,
          "lns": 0,
          "pcd": 377300,
          "rate": 0.0125,
          "sur": false,
          "tax": 1.25,
          "lvl": 2,
          "tid": 357
        },
        {
          "max": 2147483647,
          "min": 0,
          "tchg": 100,
          "calc": 1,
          "cat": "SALES AND USE TAXES",
          "cid": 1,
          "name": "Consumer Use Tax",
          "exm": 0,
          "lns": 0,
          "pcd": 377300,
          "rate": 0.06,
          "sur": false,
          "tax": 6,
          "lvl": 1,
          "tid": 357
        },
        {
          "max": 2147483647,
          "min": 0,
          "tchg": 100,
          "calc": 1,
          "cat": "SALES AND USE TAXES",
          "cid": 1,
          "name": "District Consumer Use Tax",
          "exm": 0,
          "lns": 0,
          "pcd": 377200,
          "rate": 0.0125,
          "sur": false,
          "tax": 1.25,
          "lvl": 2,
          "tid": 358
        }
      ]
    }
  ]
}
{% endhighlight %}
    </div>
  </div>
</div>


<ul class="pager">
  <li class="previous"><a href="/communications/dev-guide_rest_v2/customizing-transactions/sample-transactions/safe-harbor-override/"><i class="glyphicon glyphicon-chevron-left"></i>Previous</a></li>
  <li class="next"><a href="/communications/dev-guide_rest_v2/customizing-transactions/sample-transactions/private-line/">Next<i class="glyphicon glyphicon-chevron-right"></i></a></li>
</ul>