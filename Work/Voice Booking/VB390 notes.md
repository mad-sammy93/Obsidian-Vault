---
tags:
  - VB
  - VB-390
---



```
function render_menu_items_with_acf_data($menu_location) {
	
	$menu_items = get_menu_items_with_acf_data($menu_location); 
	if ($menu_items) { foreach ($menu_items as $menu_item) { 
		// Get ACF data for the current menu item 
		$menu_title = get_field('menu_title', $menu_item->ID);
		$menu_description = get_field('menu_description', $menu_item->ID);
		 // Check if ACF data is available 
		 if ($menu_title || $menu_description) { echo '<div class="menu-item">'; 
		 if ($menu_title) { echo '<h2>' . esc_html($menu_title) . '</h2>'; } 
		 if ($menu_description) { echo '<p>' . esc_html($menu_description) . '</p>';
	} echo '</div>';
	 } } } }
```

[[Old drift code]]



###### Steps to follow



- Import **ACF** options file

-  Add menu **Account Menu customers (EN)** 
- Assign to location **Account Menu(Customers)**


- Add menu **Account Menu editors (EN)** 
- Assign to location **Account Menu(Editor)**


- add appropriate label and link to menu items along with icons
  

  
  
  



```

function render_login_display(user = false){

var html = '';

  

if(!user){

html += '<span id="login-outline-button">'+"<?php esc_html_e('Login', 'voicebooking-login'); ?>"+'</span>';

}

else {

html += '<div data-class="mob_user" class="user-profile"><div class="left">'+

'<div class="user">'+user.firstname+

'</div></div><img src="'+user.avatar+'" alt="Users profile picture"></div>';

}

html += '<div id="login-popup"><div id="login-popup-inner">';

if(!user){

html += '<div class="top-content">';

<?php

global $WPCS;

if (ICL_LANGUAGE_CODE === 'nl') {

$register_pp_link = 'nl/registreren/account-type';

$login_pp_link = 'nl/inloggen';

} elseif (ICL_LANGUAGE_CODE === 'fr') {

$register_pp_link = 'fr/sinscrire/type-de-compte';

$login_pp_link = 'fr/connexion';

} else {

$register_pp_link = 'register/account-type';

$login_pp_link = 'login';

}

?>

html += '<a href="<?php echo PROJECT_PAGES_API . '/' . $login_pp_link; ?>" class="login_button btn btn-block btn-warning"><?php esc_html_e('Login', 'voicebooking-login'); ?></a>';

html += '<div class="register-button"> <a class="btn" href="<?php echo PROJECT_PAGES_API . '/' . $register_pp_link; ?>?ref=top-navigation&currency=<?php echo $WPCS->current_currency ?>"><?php esc_html_e('Register for free', 'voicebooking-login'); ?></a></div>';

<?php

$audition_page_id = get_theme_mod('audition_page_id', 4831);

$audition_trid = apply_filters('wpml_object_id', $audition_page_id, 'page', true, ICL_LANGUAGE_CODE);

?>

html += '<div class="audition-link"><?php esc_html_e('Voice over and looking for audition?', 'voicebooking-login'); ?> <a href="<?php echo get_the_permalink($audition_trid); ?>"><?php esc_html_e('Click here', 'voicebooking-login'); ?></a></div></div>';

}

else {

html += '<div class="login-user-content">'+

'<span class="dashboard"><a href="<?php echo PROJECT_PAGES_API; ?>/client/dashboard"><?php esc_html_e('My dashboard', 'voicebooking-login'); ?></a></span>'+

'<span class="dashboard"><a href="<?php echo PROJECT_PAGES_API; ?>/client/subscription"><?php esc_html_e('Subscriptions', 'voicebooking-login'); ?></a></span>'+

'<span class="dashboard"><a href="<?php echo PROJECT_PAGES_API; ?>/client/invoices"><?php esc_html_e('Billing', 'voicebooking-login'); ?></a></span>'+

'<span class="dashboard"><a href="<?php echo PROJECT_PAGES_API; ?>/client/settings"><?php esc_html_e('Manage profile', 'voicebooking-login'); ?></a></span>'+

'<span class="logout"><a href="<?php echo PROJECT_PAGES_API; ?>/logout"><?php esc_html_e('Logout', 'voicebooking-login'); ?></a></li></div>';

}

html += '</div></div>';

return html;

}
```

