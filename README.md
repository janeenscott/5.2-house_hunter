# 5.2 - House Hunter

So Tod really liked the Hey Neighbor apps you guys built, but after talking with his team of attorneys has decided the liability is too high. So he has a new idea!

Tod has noticed the popularity of the HGTV show Flip or Flop, and he thinks many of the viewers would really like to get into flipping homes. Tod wants an app built that allows you to drive around neighborhoods and catalog run down houses for sales. This would then allow users to find the best houses to flip.

## Objectives

### Learning Objectives

After completing this assignment, you should

- Be able to create django model forms (both create and update)
- Be able to create custom validation rules on fields that are on a django form
- Connect a django form to create/update views
- Provide client side form validation using Parsley.

## Details

### Deliverables

* A repo containing at least:
  * A django project with a `house` app
  * A `House` model
  * Create and Update forms for the `House` model.
  * Create and update views for the `House` model.
  * Server side and client side form validation.
  * Comply with pep8 and pep20

## I am a Django Developer Mode

 * Create a new django project that uses postgres
 * Create a new app called `houses`
 * Create a `Damage` model in your `houses` app
 * The model should include the following fields:
 	* type (char255) - Required
 * Register your `Damage` model with dajango admin and create the following objects:
    * Roof
    * Exterior Minor
    * Exterior Major
    * Interior Minor
    * Interior Major
 * Create a `House` model in your `houses` app
 * The model should include the following fields:
    * Damage (Many to Many Damage model)
 	* Street Address (char255) - Required
 	* Street Address 2 (char255)
 	* City (char255) - Required
 	* State (choices of US states) - Required
 	* Zip code (integer) - Required
 	* General Description (text)
 	* List Price (integer) - Required
 	* Approx Repair Cost (integer) - Required
 	* Resale Value (integer) - Required
 	* Image (Image Upload) - Required
 
 * Create a List View that shows all the `House` objects that have been added (and a link to add new houses):
   * Display the uploaded image of the house
   * Display the approximate profit (resale - (list price + repair cost))
   * Display a link to edit each house
 
 * Create house Create View that uses the model form described below
 * Create a house Update View that uses the model form described below
 
 * Create a house ModelForm:
   * The form should allow users to provide all the fields on the model
   * The image upload should allow users to pick a file from their computer
   * The form should display the options for the `damage` field as a set of checkboxes they can choose from
   * Provide client side validation with parsley to make sure all required fields have been submitted
   * Provide server side validation:
     * All required fields are submitted
     * Choice fields have a valid value
     * The general description field, if provided, should be at least 10 words long.

**Hint** Checkboxes need to be turned on in a django form. See: https://docs.djangoproject.com/en/dev/ref/forms/widgets/#django.forms.CheckboxSelectMultiple
**Hint** To make your parsley validation work for bootstrap layouts use this code:

```
$("#parsleyForm").parsley({
    errorClass: 'has-danger',
    successClass: 'has-success',
    classHandler: function(ParsleyField) {
        return ParsleyField.$element.parents('.form-group');
    },
    errorsContainer: function(ParsleyField) {
        return ParsleyField.$element.parents('.form-group');
    },
    errorsWrapper: '<span class="text-help">',
    errorTemplate: '<div></div>'
});
```

## Hey Mikey I Think He Likes It Mode
 
  * Add form validation that requires a user to select at least two damage areas.
  * Add form validation that makes sure the zip code is valid for the selected state.
 
## Caffeinated Mode
  
  * Instead of manually installing parsley, use Django Parsley (https://github.com/agiliq/Django-parsley) 
  * Write a custom form validator for parsley to validate that the uploaded image isn't bigger than 10k.
 
 
