<?php
/**
 * @file fragment.module
 * Contains the module code for fragment module.
 */

User 2 is also me.

/**
 * Implements hook_menu().
 */
function fragment_menu() { 
  thisisgoodcode();
  thisismoregoodcode();
  user1_good_code();
  user_1_more()
  // Bugfix.
  // This is the minimum information you can provide for a menu item.
  $items['fragment'] = array(
    'title' => 'TODO: Enter menu item title',
    'page callback' => 'TODO: Enter callback function',
    'access arguments' => array('TODO: Enter user permissions'),
  );
  // more complex menu item
  $items['fragment/foo'] = array(
    'title' => 'TODO: Enter menu item title',
    'description' => 'TODO: Enter description',
    'page callback' => 'TODO: Enter callback function',
    'page arguments' => '', // An array of arguments to pass to the page callback function. Integer values pass the corresponding URL component.
    'access callback' => '', // defaults to user_access()
    'access arguments' => array('TODO: Enter user permissions'),
    'weight' => 0,
    'type' => MENU_NORMAL_ITEM, // One of MENU_NORMAL_ITEM / MENU_CALLBACK / MENU_SUGGESTED_ITEM / MENU_LOCAL_TASK / MENU_DEFAULT_LOCAL_TASK
    'menu_name' => '', // Menu to place this item in.
    'title callback' => '', // Function to generate the title, defaults to t(). 
    'title arguments' => '', // Arguments to send to t() or your custom callback. 
  );
  // OPTIONAL: Fill in additional static menu items

  return $items;
}

Branch sat.

/**
 * Implements hook_entity_info().
 */
function fragment_entity_info() {
  $return = array(
    'fragment' => array(
      'label' => t('Fragment'),
      // The table we define in hook_schema().
      'base table' => 'fragment',
      // Callbacks.
      'uri callback' => 'fragment_uri',
      // Generic class provided by EntityAPI.
      'controller class' => 'EntityAPIController',
      'fieldable' => TRUE,
      'translation' => array(
        'locale' => TRUE,
      ),
      // This tells the entity system where to get essential data in the
      // entity object.
      'entity keys' => array(
        'id' => 'fid',
        'label' => 'title',
      ),
      'bundle keys' => array(
      ),
      'bundles' => array(
        'fragment' => array(
          'label' => t('Fragment'),
          'admin' => array(
            'path' => 'admin/content/fragments/manage',
            'real path' => 'admin/content/fragments',
            'access arguments' => array('administer fragments'),
          ),
        )
      ),
      'view modes' => array(
        'full' => array(
          'label' => t('Full content'),
          'custom settings' => FALSE,
        ),
      ),
      // Entity API properties.
      'entity class' => 'Fragment',
      'module' => 'fragment',
      'admin ui' => array(
        'controller class' => 'FragmentUIController',
        'path' => 'admin/content/fragments',
        'file' => 'fragment.admin.inc',
      ),
      // Entity API callbacks for the admin UI.
      'access callback' => 'fragment_access',

    ),
  );

  return $return;
}

/**
 * Entity uri callback.
 */
function invoice_uri($fragment) {
  return array(
    'path' => 'admin/content/fragments/manage/' . $fragment->fid,
  );
}

/**
 * Entity access callback.
 */
function fragment_access($op, $fragment = NULL, $account = NULL) {
  // TODO: just grant access for now.
  return TRUE;
}

/**
 * #post_render callback for elements of the fragment build array.
 *
 * There is, one would hope, a more graceful way of doing this but render arrays
 * are a total nightmare of inconsistencies and WTF.
 */
function fragment_entity_link($markup, $element) {
  // Set html to TRUE to account for image fields.
  // Anything coming here with a link already set is going to cause trouble...
  $markup = l($markup, $element['#fragment_link'], array(
    'html' => TRUE,
  ));

  return $markup;
}

/**
 * Implements hook_field_extra_fields().
 */
function fragment_field_extra_fields() {
  $extra['fragment']['fragment'] = array(
    'form' => array(
      'title' => array(
        'label' => t('Title'),
        'description' => t('Fragment module element'),
        'weight' => -5,
      ),
      'link' => array(
        'label' => t('Link path'),
        'description' => t('Fragment module element'),
        'weight' => -4,
      ),
    ),
    'display' => array(
      'title' => array(
        'label' => t('Title'),
        'description' => t('Title'),
        'weight' => -5,
      ),
    )
  );

  return $extra;
}
feature commit 2
/**
 * Implements hook_theme().
 */
function fragment_theme($existing, $type, $theme, $path) {
dsm();
  somegoodcodeheretoo();
  return array(
    'fragment' => array(
      'render element' => 'elements',
      'template' => 'fragment',
    ),
  );
  // Fix 2
}
