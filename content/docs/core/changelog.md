---
title: Changelog
description: Changelog for the Core Vendr product
---

## v1.3.0       
**Date:** 2020-09-17    
**Description:** Minor release including new features and some bug fixes / breaking changes  
---  

<changelog>
<changelog-group category="Added">  

* Added new store summary dashboard featuring a sales summary, links to pertinent actions as well as an activity log.
* Added commerce route dashboard giving summary of stores the current user has access to.
* Added analytics section to stores to provide basic analytics reporting on the stores performance.
* Added ability to handle Vendr subscription based licenses.
* Added Vendr logo to Umbraco package.

</changelog-group>
<changelog-group category="Fixed">  

* Fixed Umbraco 8.8 RC styling issues mostly around icons.

</changelog-group>
<changelog-group category="Changed">  

* `IEntityStateCache` is now no longer an injectable dependency, instead it accessed via the Unit of Work.
* List view buttons now use the outline style as per the latest Umbraco.
* `IProductCalculator` now accepts a `ProductCalculatorContext`.

</changelog-group>
<changelog-group category="Breaking">  

* `IUnitOfWork` interface now provides access to entity state cache.
* `UnitOfWork` now accepts a `VendrUnitOfWorkTransaction`.

</changelog-group>
</changelog>

## v1.2.10      
**Date:** 2020-09-11  
**Description:** Patch release with minor bug fixes mostly around the Umbraco 8.7 release  
---  

<changelog>
<changelog-group category="Fixed">  

* Fixed a styling bug in order details header that got missed in the previous release.

</changelog-group>
</changelog>

## v1.2.9      
**Date:** 2020-09-11  
**Description:** Patch release with minor bug fixes mostly around the Umbraco 8.7 release  
---  

<changelog>
<changelog-group category="Fixed">  

* Fixed a bug in the session manager remembering an order after it had been moved to finalized.
* Fixed bug in UI mot matching the same colours used by Umbraco ([#174](https://github.com/vendrhub/vendr/issues/174)).
* Fixed bug with price + store entity pickers not working correctly in Umbraco 8.7 ([#176](https://github.com/vendrhub/vendr/issues/176)).
* Fixed a series of style changes in the recently Umbraco 8.7 release.

</changelog-group>
</changelog>

## v1.2.8      
**Date:** 2020-08-21   
**Description:** Patch release with minor bug fixes / enhancements  
---  

<changelog>
<changelog-group category="Added">  

* Added new customer info panel accessible via a user icon next to the customer name to be able to display registered customer info + order history ([#129](https://github.com/vendrhub/vendr/issues/129)).
* Added helpful exception messages if you attempt to create an order but the required store default config isn't yet in place. It now tells you what needs fixing, and how to fix it ([#158](https://github.com/vendrhub/vendr/issues/158)).

</changelog-group>
<changelog-group category="Changed">  

* Use `umb-loader` component in Vendr list view rather than raw markup + css classes ([#161](https://github.com/vendrhub/vendr/issues/161)).
* Improved accessibility in a number of areas ([#162](https://github.com/vendrhub/vendr/issues/162)).
* Removed `umb-overlay` directive usage in favour of the `overlayService` ([#163](https://github.com/vendrhub/vendr/issues/163)).
* Expanded any self closing directive DOM tags as this is considered bad practice for directives ([#164](https://github.com/vendrhub/vendr/issues/164)).

</changelog-group>
<changelog-group category="Fixed">  

* Fixed bug where creating a new order via the session manager wasn't populating a default shipping country / shipping method ([#156](https://github.com/vendrhub/vendr/issues/156)).
* Fixed bug in session manager SetDefaultCurrency and SetDefaultTaxClass where exception was thrown if `applyToCurrentOrder` is `true` ([#160](https://github.com/vendrhub/vendr/issues/160)).
* Add null checks and error logs if there is a problem calculating order gift card amount if a gift card is deleted ([#167](https://github.com/vendrhub/vendr/issues/167)).
* Fixed long order line names flowing off screen. They are now truncated with ... ([#147](https://github.com/vendrhub/vendr/issues/147)).
* Fixed bug in Member Group Discount Rule throwing YSOD due to DI resource not being found. Now use `IMemberService` for everything.
* Fixed rounding issue when applying a discount amount but the order line totals calculation doesn't match the price + tax of the discount exactly.

</changelog-group>
</changelog>

## v1.2.7      
**Date:** 2020-07-29   
**Description:** Patch release with minor bug fixes / enhancements  
---  

<changelog>
<changelog-group category="Added">  

* Added payment provider feature to fetch an orders payment status from the payment gateway when an order is opened in the same way Tea Commerce does.

</changelog-group>
<changelog-group category="Changed">  

* Updated how the stock property editor loads and persists it's value so that it doesn't cause a stock update every time it's saved.
* Orders now finalize if the payment status is anything but Initialized (previously didn't finalize if the status was PendingExternalSystem).
* Pending payment status is now displayed as purple in the back office so that it's not the same colour as the canceled status.
* Updated the store entity picker to support multiple store resolution modes so that the picker can be used outside of the content section ([#141](https://github.com/vendrhub/vendr/issues/141)).

</changelog-group>
<changelog-group category="Fixed">  

* Fixed bug when creating US country regions from preset ([#159](https://github.com/vendrhub/vendr/issues/159)).
* Fixed issue with payment provider continue/cancel/error URLs escaping querystrings ([#157](https://github.com/vendrhub/vendr/issues/157)).
* Fixed &lt;= price discount rule not displaying correct symbol ([#155](https://github.com/vendrhub/vendr/issues/155)).

</changelog-group>
</changelog>

## v1.2.6     
**Date:** 2020-07-02   
**Description:** Patch release with minor bug fixes / enhancements and some breaking changes 
---  

<changelog>
<changelog-group category="Fixed">  

* Thawing prices now causes existing, unfinalized orders to recalculate and re-freeze prices at the current rate ([#145](https://github.com/vendrhub/vendr/issues/145)).
* Fixed YSOD when applying a discount with multiple rewards for the same price target. Applied discounts now accumulate all rewards per price type ([#136](https://github.com/vendrhub/vendr/issues/136)).
* Fixed bug in discounts where the "Block discount if previous discounts already apply" setting was not being honored ([#142](https://github.com/vendrhub/vendr/issues/142)).
* Fixed bug in discounts where Order Total based percentage discounts were not being applied ([#143](https://github.com/vendrhub/vendr/issues/143)).
* Fixed error when creating an order and adding order lines in the same UoW. This ultimately came down to the price freezing logic freezing prices too early. For new orders, prices are now frozen after the initial save ([#140](https://github.com/vendrhub/vendr/issues/140)).
* Fixed issue in migrations where some installs seem to convert unique indexes into unique constraints and so a YSOD is thrown when attempting to drop the index. We now check to see if a constraint exists first and then perform the appropriate task ([#116](https://github.com/vendrhub/vendr/issues/116)).

</changelog-group>
<changelog-group category="Breaking">  

* `IShippingCalculator` methods now take in a `ShippingCalculatorContext` with a reference to the current order / order calculation should one be available ([#146](https://github.com/vendrhub/vendr/issues/146)).
* `IPaymentCalculator` methods now take in a `PaymentCalculatorContext` with a reference to the current order / order calculation should one be available ([#146](https://github.com/vendrhub/vendr/issues/146)).

</changelog-group>
</changelog>

## v1.2.5    
**Date:** 2020-06-17   
**Description:** Patch release with minor bug fixes / enhancements  
---  

<changelog>
<changelog-group category="Added">  

    
* Added license warning message to gift cards, discounts and store settings sections.


</changelog-group>
<changelog-group category="Fixed">  

* Fixed issue where sort dialog displays the wrong error message if there is an error whilst sorting ([#131](https://github.com/vendrhub/vendr/issues/131)).
* Fixed issue where Dates were incorrect due to use of DateTime.Now rather than DateTime.UtcNow  ([#134](https://github.com/vendrhub/vendr/issues/134)).
* Fixed rounding issue in order calculation  ([#126](https://github.com/vendrhub/vendr/issues/126)).
* Fixed issue with the entity cache storing null values which shouldn't be allowed.
* Fixed issue where setting an explicit sort order on a new entity would be ignored on save.
* Fixed regression issue from 1.2.3 where loading orders from the database was switching the order id and currency id of the order causing calculation problems.
* Fixed issue with spelling mistake in discount rules / reward configs for `Amounts Include Tax` properties ([#135](https://github.com/vendrhub/vendr/issues/135)).
* Fixed issue with discounts not maintaining their sort order when loading from the database ([#132](https://github.com/vendrhub/vendr/issues/132)).

</changelog-group>
<changelog-group category="Changed">  

* Deprecated "Master" terminology in the code base so `MasterRelation` is now `ProductSource` (This is currently just deprecated so the existing `MasterRelation` will still work, but moving forward `ProductSource` will be the recommended terminology).
* Updated the payment methods create dialog to exclude any payment providers marked with an `[Obsolete]` attribute. Obsolete payment providers can still be used, but they won't be selectable for new payment methods.
* Removed the sort option from the Gift Cards section as gift cards aren't sortable ([#131](https://github.com/vendrhub/vendr/issues/131)).
* Made the `Order.InitializeTransaction` method public to allow people to create and finalize a transaction in code without having to go via a payment gateway.
* Store `Create` method extended to make store auto population configurable. This is needed for Vendr.Deploy.

</changelog-group>
</changelog>


## v1.2.4   
**Date:** 2020-06-12  
**Description:** Patch release with minor bug fixes / enhancements and some minor breaking changes 
---  

<changelog>
<changelog-group category="Added">  

    
* Added support for `UmbracoLicensesDirectory` app setting to define where licenses are located ([#119](https://github.com/vendrhub/vendr/issues/119)).
* Added `CanProcessOrder` method to payment providers so that payment providers can pre-check whether they would be capable of processing a given order.


</changelog-group>
<changelog-group category="Fixed">  

* Fixed issue where it wasn't possible to update a products stock back to the previously entered stock level ([#127](https://github.com/vendrhub/vendr/issues/127)).
* Fixed issue where multiple operations within a single UoW were not being persisted due to stale state not getting updated correctly ([#128](https://github.com/vendrhub/vendr/issues/128)).
* Fixed issue with the `Extract` helper method throwing an exception if the give item to extract couldn't be found.
* Fixed issue where null order / order line properties would cause persistence error.

</changelog-group>
<changelog-group category="Changed">  

* Updated the percentage amount discounts rewards to only allow positive percentage values ([#113](https://github.com/vendrhub/vendr/issues/113)).

</changelog-group>
<changelog-group category="Breaking">  

    
* Renamed the `Persistance` namespace to the correct `Persistence` spelling. This is a breaking change, but people shouldn't be using the persistence resources directly.
* Moved `ValidationError` to `Models` namespace. This is a breaking change, but people shouldn't be using the `ValidationError` model directly.
* With the introduction of the `UmbracoLicensesDirectory` app setting, if you are running on Umbraco Cloud and have a license installed, because Umbraco Cloud auto sets this setting to `~\App_Plugins\UmbracoLicenses\` you will need to move your license files from the `App_Data` folder to this new location.


</changelog-group>
</changelog> 


## v1.2.3  
**Date:** 2020-06-05  
**Description:** Patch release with minor bug fixes / enhancements  
---  

<changelog>
<changelog-group category="Fixed">  

* Fixed issue with recent gift card config settings not being copied when a store is deep cloned.
* Fixed issue with store "allowed users" not persisting due to incorrect variable name in views.
* Fixed issue where domain events that affect the saving entity model were not being persisted due to a variable reference issue and deep comparisons not working.
* Fixed issue with the sort dialog close button not working ([#123](https://github.com/vendrhub/vendr/issues/123)).
* Fixed issue where deleted gift cards were still showing in list view ([#124](https://github.com/vendrhub/vendr/issues/124)).
* Fixed issue where stock values were being cached at the page level where they should be at the request level ([#125](https://github.com/vendrhub/vendr/issues/125)).

</changelog-group>
<changelog-group category="Changed">  

* Only show payment / shipping "via" in the back-office if a payment / shipping method is known.
* Added script to NuGet packages to auto increment client dependency version.
* Order calculation now rounds prices to the currencies defined decimal places level after each calculation step in order to prevent rounding issues ([#126](https://github.com/vendrhub/vendr/issues/126)).
* Payment Provider cancel, continue and callback URL hashes now include the actual URL, and not just the reference as part of the hash. This is to prevent tampering of the the URLs.
* Session cookies are now flagged as `HttpOnly` (this can be disabled by setting an app setting `Vendr:Cookies:HttpOnly` to `false`), and when the site is accessed over https, also flagged as `Secure`. This is to protect the session cookies from being hijacked from malicious entities. 
* The current finalized order is now stored in it's own session cookie with a limited lifetime of 5 minutes providing enough time to display a confirmation page, but no longer persisting until a new order took it's place.

</changelog-group>
</changelog> 

## v1.2.1/2  
**Date:** 2020-05-28  
**Description:** Patch release with minor bug fixes / enhancements   
---  

<changelog>
<changelog-group category="Fixed">  

    
* Fixed bug in discount service preventing discount / gift cards from being redeemed 🤦‍♂️
* Reverted fix for ([#116](https://github.com/vendrhub/vendr/issues/116)) as it was preventing clean installs so needs investigating further 🤦‍♂️

</changelog-group>
</changelog> 


## v1.2.0  
**Date:** 2020-05-28  
**Description:** Minor version release predominantly for the Gift Cards feature with a few bug fixes too  
--- 

<changelog>
<changelog-group category="Added">  

    
* Added gift cards feature which includes a new sub-section in the commerce section along with the ability to create gift cards manually and additional automations for automatically creating gift cards and sending gift card emails when a gift card is purchased.
* Added `IGiftCardCodeGenerator` to allow for custom gift card code generation strategy.
* Added Zero Value payment provider in core to allow the passing through of orders who's final value is 0 and thus no payment needs to be taken. This will be up to the implementer however to setup and select this payment method accordingly.
* Added gift card service methods to the global `IVendrApi` helper.
* Added support of dynamic lambda statements in the syntax of `{Model.Value}` in email template subject lines ([#107](https://github.com/vendrhub/vendr/issues/107)).
* Added validation to the `AddProduct` method to ensure a price for the order currency exists.
* Added `_ViewStart.cshtml` file to the Vendr views folder to reset any global layout that might have been defined ([#117](https://github.com/vendrhub/vendr/issues/117)).


</changelog-group>
<changelog-group category="Fixed">  

    
* Fixed NullReference exception when adding a product to an order when missing a price ([#112](https://github.com/vendrhub/vendr/issues/112)).
* Fixed a number of migration SQL errors when upgrading using SQL Server ([#116](https://github.com/vendrhub/vendr/issues/116)).
* Fixed error with discount property rule not working correctly when a property doesn't exist ([#115](https://github.com/vendrhub/vendr/issues/115)).
* Fixed bug with discount code validation incorrectly reporting the discount code is already in use.


</changelog-group>
<changelog-group category="Changed">  

    
* Store configuration now has additional gift card configuration fields.
* Email Templates now have a category used to filter the email templates to display in "send email" dialogs.
* Updated store create pipeline to auto create the default gift card email.
* Updated store create pipeline to assign generated emails to the relevant categories.
* Send email dialogs now have an ability to override the `To` address before sending.
* Improved the `PricePropertyValue` models `HasValue` method to also check for null values.
* Updated the `UmbracoProductSnapshot.Prices` property to check for values for the given currency before assuming it has a value.


</changelog-group>
<changelog-group category="Breaking">  

    
* `IProductAdapater` interface now has a new `IsGiftCard` property.


</changelog-group>
</changelog>

## v1.1.4
**Date:** 2020-05-19   
**Description:** Patch release with minor bug fixes / enhancements  
--- 

<changelog>
<changelog-group category="Fixed">  

    
* Fixed javaScript error when refreshing order list view after an order is deleted ([#96](https://github.com/vendrhub/vendr/issues/96)).
* Fixed formatting issue in table view selection message where `X of Y` message was being displayed without spaces.
* Fixed YSOD when deleting an order line that has discounts applied to it  ([#98](https://github.com/vendrhub/vendr/issues/98)).
* Fixed order lines being limited to a max of 100 quantity ([#101](https://github.com/vendrhub/vendr/issues/101)).
* Fixed YSOD in back-office when displaying the transaction info dialog when some keys have an empty value ([#104](https://github.com/vendrhub/vendr/issues/104)).
* Fixed YSOD when adding a sub order line to a bundle ([#106](https://github.com/vendrhub/vendr/issues/106)).


</changelog-group>
</changelog>

## v1.1.3
**Date:** 2020-05-06   
**Description:** Patch release with minor bug fixes / enhancements  
--- 

<changelog>
<changelog-group category="Fixed">  

    
* Patch release dll timestamp not formatted in the correct way.
* Fixed bug in TaxClassRepository.GetIdByAlias method which had a malformed SQL statement.
* Fixed NuGet install script not working correctly in directories containing spaces.


</changelog-group>
<changelog-group category="Changed">  

    
* When saving a product node with a stock property, only sync the value back to the stock database table if the property is dirty ([#93](https://github.com/vendrhub/vendr/issues/93)).


</changelog-group>
</changelog>

## v1.1.2  
**Date:** 2020-05-05   
**Description:** Patch release with minor bug fixes / enhancements  
--- 

<changelog>
<changelog-group category="Added">  

    
* Added `*.xip.io`, `*.nip.io` and `*.sslip.io` as valid test domains.
* Added strongly typed value converter for the store entity picker property editor.
* Added missing validation events for Discount code add/update/remove.
* Added validation events to all entities to validate the uniqueness of aliases / codes.
* Added `Exists` methods to all entity services to make it easier to check for the existence of an entity.


</changelog-group>
<changelog-group category="Fixed">  

    
* Fixed bug in product uniqueness logic throwing a YSOD if you add a product with no uniqueness properties after one that has is already in the cart ([#88](https://github.com/vendrhub/vendr/issues/88)).
* Fixed build script formatting the patch release timestamp incorrectly.
* Fixed YSOD when removing items from a cart and using SQL CE. This was due to a SQL statement that doesn't work on SQL CE. Now updated to work across the board ([#89](https://github.com/vendrhub/vendr/issues/89)).
* Fixed bug where discount codes declared on deleted discounts couldn't be reused ([#91](https://github.com/vendrhub/vendr/issues/91)).
* Discount aliases are now validated before save and display a friendly error message ([#91](https://github.com/vendrhub/vendr/issues/91)).


</changelog-group>
<changelog-group category="Changed">  

    
* Changed picker property editor 'add' buttons to use a button element, rather than a link tag ([#86](https://github.com/vendrhub/vendr/issues/86)).
* Changed table view 'create' buttons to use a button element, rather than a link tag ([#87](https://github.com/vendrhub/vendr/issues/87)).
* Implemented friendlier display of validation errors ([#91](https://github.com/vendrhub/vendr/issues/91)).


</changelog-group>
</changelog>

## v1.1.1  
**Date:** 2020-04-29  
**Description:** Patch release with minor bug fixes / enhancements  
--- 

<changelog>
<changelog-group category="Fixed">  

    
* Fixed issue with v1.1.0 NuGet package not copying email templates to the Views folder 🤦‍♂️.


</changelog-group>
</changelog>

## v1.1.0 
**Date:** 2020-04-29  
**Description:** Minor release with new features and some minor bug fixes / enhancements
--- 

<changelog>
<changelog-group category="Added">  

    
* Added "Unlimited" checkbox to discount codes to allow them to have unlimited usage ([#50](https://github.com/vendrhub/vendr/issues/50)).
* Added basic Order/Payment Status filters to Order list ([#63](https://github.com/vendrhub/vendr/issues/63)).
* Added escape key shortcut to close Discount rule/rewards settings editor dialog ([#60](https://github.com/vendrhub/vendr/issues/60)).
* Added feedback when copying order details to clipboard ([#22](https://github.com/vendrhub/vendr/issues/22)).
* Added new store entity picker property editor to merge together all store entity pickers. Tax Class picker is now obsolete in favour of this new picker.
* Added email templates for the default Confirmation / Error emails.


</changelog-group>
<changelog-group category="Fixed">  

    
* Fixed YSOD when accessing transaction info for an order where the Payment Provider no longer existed. Now perform null checks on data ([#58](https://github.com/vendrhub/vendr/issues/58)).
* Fixed issue with NuGet packages not copying content files on upgrade. Added a PowerShell script to perform the copy.
* Fixed bug where customer details weren't being persisted into the dedicated fields in the database table (they are still present in the properties collection where they are referenced from 99% of the time) ([#85](https://github.com/vendrhub/vendr/issues/85)).


</changelog-group>
<changelog-group category="Changed">  

    
* Rule / Reward builders now support infinite editing when creating a rule so closing the editor via the 'close' link now goes back to the rule / reward picker. ([#81](https://github.com/vendrhub/vendr/issues/81)).


</changelog-group>
<changelog-group category="Removed">  

    
* Removed code for shipping method / payment method picker property editors in favour of the new store entity picker. These were never made public as actual property editors, as they were only used by the rule / reward builder so this won't be classed as a breaking change.


</changelog-group>
</changelog>

## v1.0.3 
**Date:** 2020-04-24  
**Description:** Patch release with minor bug fixes / enhancements
--- 

<changelog>
<changelog-group category="Added">  

    
* Added missing Product discount rule to discounts rule builder ([#76](https://github.com/vendrhub/vendr/issues/76)).
* Added basic Order Line Amount Reward that applies to all Order Lines.


</changelog-group>
<changelog-group category="Fixed">  

    
* Product prices now thaw when the last product of a type is removed from the cart ([#71](https://github.com/vendrhub/vendr/issues/71)).
* Fixed YSOD when saving a property with a null value. Property is now removed if the value is null  ([#78](https://github.com/vendrhub/vendr/issues/78)).


</changelog-group>
<changelog-group category="Changed">  

    
* Changed the name of the Products Order Line Amount Reward to Order Line (with Product) Amount Reward as it's more descriptive of it's purpose.


</changelog-group>
</changelog>

## v1.0.2 
**Date:** 2020-04-15  
**Description:** Patch release with minor bug fixes / enhancements
--- 

<changelog>
<changelog-group category="Added">  

    
* Added ability to delete an order from the action menu.
* Added permission checks to all entity controller actions.


</changelog-group>
<changelog-group category="Fixed">  

    
* Fixed ability to delete orders ([#49](https://github.com/vendrhub/vendr/issues/49)).
* Fixed issue with orders not finalizing if an error occurs sending emails. Email sending is now wrapped in a try catch that logs errors to the error log instead ([#52](https://github.com/vendrhub/vendr/issues/52)).
* Fixed bug in EmailTemplateService.SendEmail where it wasn't sending to the supplied To email address unless "Send to Customer" on the email template was checked. This setting now only applies if you call the SendEmail method version that accepts an Order. The signature with the explicit toEmailAddress parameter will always send to the provided email address ([#54](https://github.com/vendrhub/vendr/issues/54)).
* Percentage reward inputs now only accept decimals ([#59](https://github.com/vendrhub/vendr/issues/59)).
* Fixed property discount rule, property alias field description describing the wrong thing ([#62](https://github.com/vendrhub/vendr/issues/62)).


</changelog-group>
<changelog-group category="Changed">  

    
* Changed payment status colours so Authorized is now blue and Refunded is orange so that Refunded doesn't look like an error ([#61](https://github.com/vendrhub/vendr/issues/61)).


</changelog-group>
</changelog>

## v1.0.1 
**Date:** 2020-04-06  
**Description:** Patch release with minor fixes found post launch
--- 

<changelog>
<changelog-group category="Fixed">  

    
* Fixed wrong license URL displayed in installer.
* Fixed stock input field not allowing a stock level greater than 100 ([#44](https://github.com/vendrhub/vendr/issues/44)).
* Fixed stock input field rounding decimal stock levels on save ([#45](https://github.com/vendrhub/vendr/issues/45)).

</changelog-group>
<changelog-group category="Changed">  

    
* Updated all caches to use a `GetOrAddIfNotNull` method to ensure null entities don't end up in the internal cache.


</changelog-group>
</changelog>

## v1.0.0  
**Date:** 2020-03-30  
**Description:** Initial Vendr release 