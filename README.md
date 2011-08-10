Yii-User Installation
=====================

Download
--------

Download or checkout (SVN/Git) from http://yii-user.2mx.org and unpack files in your project/protected

Configure
---------

Change your config:

    return array(
        #...
        // autoloading model and component classes
        'import'=>array(
            'application.models.*',
            'application.components.*',
            'application.modules.user.models.*',
            'application.modules.user.components.*',
        ),
        #...
        'modules'=>array(
            'user'=>array(
                'hash' => 'md5',                                     # encrypting method (php hash function)
                'sendActivationMail' => true,                        # send activation email
                'loginNotActiv' => false,                            # allow access for non-activated users
                'autoLogin' => true,                                 # automatically login from registration
                'registrationUrl' => array('/user/registration'),    # registration path
                'recoveryUrl' => array('/user/recovery'),            # recovery password path
                'loginUrl' => array('/user/login'),                  # login form path
                'returnUrl' => array('/user/profile'),               # page after login
                'returnLogoutUrl' => array('/user/login'),           # page after logout
            ),
        ),
        #...
        // application components
        'components'=>array(
        #...
            'db'=>array(
            #...
                'tablePrefix' => 'tbl_',
            #...
            ),
            #...
            'user'=>array(
                // enable cookie-based authentication
                'class' => 'WebUser',
                'allowAutoLogin'=>true,
                'loginUrl' => array('/user/login'),
            ),
        #...
        ),
        #...
    );

Install
-------

Run command: yiic migrate --migrationPath=application.modules.user.migrations

Login
-----

Default users:

* admin/admin
* demo/demo