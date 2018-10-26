---
layout: page
title:  Chapter 5.6 - Tax Override
product: communications
doctype: comms_dev_guide
chapter: reference
nav: apis
disqus: 0
---

<ul class="pager">
  <li class="previous"><a href="/communications/dev-guide/reference/line-item/"><i class="glyphicon glyphicon-chevron-left"></i>Previous</a></li>
  <li class="next"><a href="/communications/dev-guide/reference/safe-harbor-override/">Next<i class="glyphicon glyphicon-chevron-right"></i></a></li>
</ul>

<h3>Tax Override</h3>

The <code>TaxOverride</code> object allows the user to change <b>tax rates</b>:

<div class="mobile-table">
  <table class="styled-table">
    <thead>
      <tr>
        <th>Key</th>
        <th>Value</th>
      </tr>
    </thead>
    <tbody>
      <tr>
        <td><code>loc</code></td>
        <td>
          <a class="dev-guide-link" href="/communications/dev-guide/reference/location/"><code>[Location]</code></a>
        </td>
      </tr>
      <tr>
        <td><code>scp</code></td>
        <td>
          <code>[int]</code> Scope to which the override is applied:  Country, State, County, or City
          <ul class="dev-guide-list">
            <li><code>0</code>: Country</li>
            <li><code>1</code>: State</li>
            <li><code>2</code>: County</li>
            <li><code>3</code>: City</li>
          </ul>
        </td>
      </tr>
      <tr>
        <td><code>tid</code></td>
        <td>
          <code>[int]</code> Tax Type ID for the override
          <br>
          <br>
          For a list of Tax Type IDs, see the <a class ="dev-guide-link" href="/communications/dev-guide/getting-started/environments-endpoints/"><code>/api/v2/afc/taxtype/{taxType}</code> endpoint.</a>
        </td>
      </tr>
      <tr>
        <td><code>lvl</code></td>
        <td>
          <code>[int]</code> Tax Level for the override
          <ul class="dev-guide-list">
            <li><code>0</code>: Federal</li>
            <li><code>1</code>: State</li>
            <li><code>2</code>: County</li>
            <li><code>3</code>: City</li>
          </ul> 
        </td>
      </tr>
      <tr>
        <td><code>lvlExm</code></td>
        <td>
          <code>[bool]</code> Level Exemptible
          <ul class="dev-guide-list">
            <li><code>true</code>: Level Exemptible</li>
            <li><code>false</code>: Not Level Exemptible</li>
          </ul>
        </td>
      </tr>
      <tr>
        <td><code>brkt</code></td>
        <td>
          <a class="dev-guide-link" href="/communications/dev-guide/reference/tax-bracket/"><code>[TaxBracket]</code></a>
        </td>
      </tr>
    </tbody>
  </table>
</div>
<br>

<h3>Example</h3>

{% highlight json %}
"ovr": [
    {
      "loc": {
        // Location
      },
      "scp": 1,
      "tid": 25,
      "lvl": 2,
      "lvlExm": true,
      "brkt": [
        {
          "rate": 0.25,
          "max": 0
        }
      ]
    }
  ],
{% endhighlight %}

<ul class="pager">
  <li class="previous"><a href="/communications/dev-guide/reference/line-item/"><i class="glyphicon glyphicon-chevron-left"></i>Previous</a></li>
  <li class="next"><a href="/communications/dev-guide/reference/safe-harbor-override/">Next<i class="glyphicon glyphicon-chevron-right"></i></a></li>
</ul>