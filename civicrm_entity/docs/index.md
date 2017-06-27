# CiviCRM Entity
CiviCRM Entity is a suite [Drupal](https://www.drupal.org/) modules which closely integrates [CiviCRM](https://civicrm.org) with Drupal by exposing [CiviCRM API](https://docs.civicrm.org/dev/en/latest/api/) entities as Drupal [entity types](https://www.drupal.org/docs/7/api/entity-api/an-introduction-to-entities), and adding other integration functionality. Drupal Core and any module that uses the [Entity API](https://www.drupal.org/entity) will be able to access and manipulate CiviCRM data as if it was native to Drupal.

This means modules such as [Rules](https://www.drupal.org/project/rules), [Entity Reference](https://www.drupal.org/project/entityreference), and [100s of other modules](https://www.drupal.org/project/project_module/?f%5B0%5D=&f%5B1%5D=&f%5B2%5D=&f%5B3%5D=drupal_core%3A103&f%5B4%5D=sm_field_project_type%3Afull&f%5B5%5D=&text=entity&solrsort=score+desc&op=Search) can be used in conjunction with CiviCRM to enhance and expand the functionality of the website.  

## Introduction
This guide provides documentation for installation, basic usage and configuration, site building tips and tricks, and custom development with the Drupal Entity API for CiviCRM. 

Whether you are a novice Drupal user, an advanded site administrator, or a developer, CiviCRM Entity provides a large tool chest to enhance, expand, and customize your CiviCRM integration. 


## Installation
### Requirements
CiviCRM Entity requires:

- Drupal 7
- CiviCRM 4.6 or 4.7
- Entity API

### Download
Download CiviCRM Entity from its project page on Drupal.org. 

### Manual Installation
1. Place the civicrm_entity directory into the sites/all/modules directory OR if using Drupal multisite, the site specific sites/YOURSITE.com/modules directory
1. Login as an administrator and navigate to [site_root]/admin/modules
1. Find CiviCRM Entity module group, and check the box next to CiviCRM Entities.
1. Click Save

### Drush Installation
In your Drupal site document root directory type

1. drush dl civicrm_entity
2. drush en civicrm_entity


## Features
The main CiviCRM Entity module is required for all sub modules. The main module provides the fundamental integration, providing:

- exposure of CiviCRM data as Drupal entity types.
- Drupal native add/edit/delete forms for all exposed entity types
- ability to add Drupal Fields to CiviCRM data
- support for [Display Suite](https://www.drupal.org/project/ds)
- Rules events and actions
- Views integration for entity types not covered by the CiviCRM Core module
- Extendible to support additional or custom CiviCRM entities

## Sub modules
Several modules are bundled with CiviCRM Entity which provide additional features and integration with other Drupal modules. 

### CiviCRM Entity Actions
Declares Drupal Actions to use with CiviCRM entity types for use with [Views Bulk Operations](https://www.drupal.org/project/views_bulk_operations)

Use to perform operations on custom generated lists of CiviCRM entities. Views Buk Operations action batching allows massive operations without php memory or timeout errors.

*Requires* [Entity Reference Autocomplete](https://www.drupal.org/project/entityreference_autocomplete)

### CiviCRM Entity Views Extras
Provides additional Views relationships or other handlers for newly exposed entities such as Price Sets, Price Fields, Price Field Values and more.

### CiviCRM Entity Inline
Provides integration with the Drupal module, Inline Entity Form. Used by Entity Reference, and CiviCRM Entity Reference fields to provide a widget for editing referenced entities inline from the parent form.

*Requires* [Inline Entity Form](https://www.drupal.org/project/inline_entity_form)

### CiviCRM Entity Reference
Provides a CiviCRM Entity Reference field type.  This field type is very similar to the standard Entity Reference field, but acts as a "remote reference field", loading the referenced entities directly from the CiviCRM database and stores no values in the Drupal field tables. 

This is used to create or edit a contact's CiviCRM addresses,emails, phone numbers, websites, from Drupal contact edit pages, and Locations Block addresses from CiviCRM Events, with the consistent and familiar Inline Entity Form widgets. Many other combinations of references are possible.

Everything you do with a CiviCRM Entity Reference field in Drupal will be immediately reflected in the standard CiviCRM adminstration pages.

*Requires* CiviCRM Entity Inline

### CiviCRM Entity Price Set Field
CiviCRM Entity Price Set field provides a new field type to your Drupal installation.  

When configured to display on the Event view pages, this field generates an Ajax powered registration form that supports:

-Registering multiple Participants
-Uses the event’s price set and all price fields of any type
-Pay later or credit card transactions utilizing CiviCRM’s payment processing
-Supports free events
-Renders and submits the CiviCRM Profiles configured for the event
-Default values for the profile fields corresponding to the logged in user’s contact information
-Customizable Ajax confirmation and thank you panes
-Utilizes the event’s settings such as “Is paid event?”, dedupe rules, etc..
-Test or Live transactions
-Supports the events Max Participants setting
-Customizable with hooks, standard Drupal theme practices

This field provides a default, simple price set edit widget, which allows admins to edit the first price field in the price set.  Further development is necessary to allow edting all properties and price fields of the set but foundation is laid.

Currently only event registrations are supported, but plans for extending this module to contribution pages are underway and will come in stages.

*Requires* CiviCRM Entity Profile

### CiviCRM Entity Profile
Provides some supporting API for Profile form generation and submissions by the Price Set field and a field type 'CiviCRM Entity Profile' that can only be added to the Event entity type. 

By creating instances of this field type on the event entity type, you can allow admins to select profiles to be used for the stock CiviCRM event registration pages, or for use in the Price Set field on-page registration form. This is similar functionailty to the "Profiles" tab on the stock CiviCRM event edit page.

### CiviCRM Entity Discount
Provides a CiviCRM Entity Discount field type, which can be added to the Event entity type. This field type provides a multi-valued field widget that allows admins to easily configure discounts that are used by the Price Set field registration form. Discounts can be configured for individual price fields, be percentage or flat amounts, and be for specific user roles.

### CiviCRM Entity Group Assign
Provides a CiviCRM Entity Contact Group Assign Field Type.  This field type has an edit widget for adding/removing a contact to a selected list of groups. Site builders can add multiple fields of this type on the Contact entity, configuring each field to toggle a different set of groups, and use either checkboxes or radios. In this way admins can create easy to understand, custom sets of groups for content editors to toggle for contacts. A wide variety of custom use cases can be set up without any code.

### CiviCRM Case Activity Reference Field
Similary to the CiviCRM Entity Reference field, but provides a specialized remote reference field type for creating and editing Activities from the CiviCRM Case entity type edit form.

### CiviCRM Entity Search API
Provides code to help make CiviCRM entity types indexable by the [Search API](https://www.drupal.org/project/search_api) module

### CiviCRM Entity Contact Assign Relationship to Contact
Provides a field type to allow custom sets of creating relationships to other contacts. Has field settings to select what type of relationship to create, and set what contacts are available to create the relationship to. Widgets for radio buttons and checkboxes.

### CiviCRM Entity Contact Assign Relationship of Type
Provides a field type to allow creating sets of relationships from the contact to another contact.  Field settings to select which contact to create the relationship to, and allow limiting the list of relationship types. Widgets for radio buttons and checkboxes.