# CakePHP Captcha Plugin for CakePHP 3.5.*

**Image captcha, Math captcha and Google-recaptcha support for CakePHP**

A demo can be found here (coming soon)

For questions queries please visit this link (coming soon)

## Installation

**Install via Composer**
(coming soon.. skip to download option)

**Install via Download**
Download and copy all files to your cakephp 3 application, to new captcha folder in your app's <ROOT>/plugins/ folder

## Configuration

1. Load **Captcha** plugin.

	Place ```Plugin::load('Captcha', ['routes' => true, 'autoload' => true]);``` in your application's **bootstrap.php** file.

2. Load **Capthca component**

	Place ```$this->loadComponent('Captcha.Captcha');``` in your controllerr's **initialize** function

3. Add Behavior to your Model/Table

	Place  ```$this->addBehavior('Captcha.Captcha', ['field'=>'<fieldname>'])``` in your **Model** (Table class)

4. Create an input field in your view's **form** as:

	```echo $this->Captcha->create('<fieldname>');```

5. In your controller in which your form data is processed, place:

	```$this->Users->setCaptcha('<fieldname>', $this->Captcha->getCode('<fieldname>'));```

	just before patching entity. For example:

	```
	$this->Users->setCaptcha('securitycode', $this->Captcha->getCode('securitycode'));
$user = $this->Users->patchEntity($user, $this->request->data);
	```
	
	
That should be it.

## Known Issues:

1. **Headers already sent** issue. The component uses php's `header()` function to send or generate captcha image as raw HTML output. Make sure there is no output generated before the create() function in your component. It is common error to have spaces, tags or empty space in your files which would cause rending no image in the captcha.

2. **GD library** and True Type Font (**TTF**) support extensions are enabled in PHP.

3. This captcha script uses three font faces, **anonymous**, **droidsans** and **ubuntu**  to generate fonts in the captcha images. These font faces are placed in the **captcha/src/Lib/Fonts** of this download. I have seen that these font files are corrupted in some downloads. If you see font not found error in your error logs and captcha are failed to generate, try downloading these font faces from their respective sources and replace them in the mentioned folder.

## Updates

No update available

## Layout

Three basic options, image captcha, math captcha and google-recaptcha

Check older version for more options here.. These should be valid in this version as well.
