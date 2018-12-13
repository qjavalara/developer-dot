---
layout: post
title: AvaTax API 18.12 Patch Notes
description: Release Notes for the December 2018 update to the AvaTax API
relevantapimethods: ListTaxCodes, BuildTaxContentFile, BuildTaxContentFileForLocation
date: 2018-12-13 16:00
author: Qijing Yu
comments: true
categories: [avatax, patch notes]
product: blog
doctype: blog
disqus: 1
---

This article is about the December 2018 monthly update to the AvaTax API.

<div class="mobile-table">
    <table class="styled-table">
        <tr>
            <th>Environment</th>
            <th>URL</th>
            <th>Release Date</th>
        </tr>
        <tr>
            <td>Sandbox</td>
            <td><a href="https://sandbox-rest.avatax.com">https://sandbox-rest.avatax.com</a></td>
            <td>2018-12-17</td>
        </tr>
        <tr>
            <td>Production</td>
            <td><a href="https://rest.avatax.com">https://rest.avatax.com</a></td>
            <td>2019-01-07</td>
        </tr>
    </table>
</div>

<h3>Sandbox Testing Window</h3>

The AvaTax release schedule includes a preview period where the latest software is available for integration testing in the [AvaTax Sandbox Environment](https://sandbox-rest.avatax.com) two weeks before launching to production. If your engineering team would like a sandbox account for integration testing purposes, please contact your account manager or [open a support ticket](https://help.avalara.com/Directory/Contact_Avalara/Submit_a_Case).

<h3>Advanced Items Setup</h3>

In addition to existing basic configurations for Items, we are now allowing more advanced settings, including:

<ul class="normal">
    <li>Items can be tagged into multiple classification systems. As opposed to Avalara tax code being the only way of classifying your item, we are now supporting more than 100 classification systems recognized worldwide, including HTS, TARIC, etc. We are also continuing supporting Avalara Tax Code with a system code of `AVATAXCODE`.</li>
    <li>Items can be set up with parameters, which were previously only allowed in transactions. Calling [CreateTransaction]|(/api-reference/avatax/rest/v2/methods/Transactions/CreateTransaction) with a pre-configured item with parameters will allow your transaction request a lot cleaner.</li>
</ul>

<h3>Definition APIs in supporting configuring Items</h3>

In assisting setting up your items to facilitate your transactions, we are providing a suite of new definition APIs:

[ListParametersByItem](/api-reference/avatax/rest/v2/methods/Definitions/ListParametersByItem) Different than the existing [ListParameters]|(/api-reference/avatax/rest/v2/methods/Definitions/ListParameters) API which provides all available parameters recognized in Avalara system, this API provides you the more refined result set that are relevant to your profile setup (service subscriptions, nexus configuration and items).
[ListProductClassificationSystems](/api-reference/avatax/rest/v2/methods/Definitions/ListProductClassificationSystems) This APIs provides all classification systems recognized by Avalara.
[ListProductClassificationSystemsByCompany](/api-reference/avatax/rest/v2/methods/Definitions/ListProductClassificationSystemsByCompany) Different than the API above, this API returns the more refined result set that are relevant to your profile setup (nexus configurations).

<h3>Swagger loading time is improved</h3>

We improved Swagger loading time by pre-compiling the swagger.json file and cached it in memory.

<h3>Other Fixes and Improvements</h3>

<ul class="normal">
    <li>Enhance error code handling for Onboarding requests</li>
    <li>Improve error messages for the postal code rate file API</li>
    <li>Improve error message from CreateTransaction and SettleTransaction</li>
    <li>Fix TaxContent API behavior for certain county/country jurisdictions</li>
    <li>Fix issue where parameters listed in CreateTransaction broke if separated by a space</li>
    <li>Fix issue where filtering by date range of 1900-01-01 results in an unhandled error</li>
    <li>Fix unhandled exception in CommitTransaction and UncommitTransaction</li>
</ul>