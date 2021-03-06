TemplateStubs
=============

ProcessWire module that generates stub classes for IDE support.

This is a useful tool for Template development for those using IDEs with static
analysis, such as PhpStorm, NetBeans, etc.

The module generates a file named "stubs.php" in the TemplateStubs folder, so
make sure this folder is write-enabled. The entire documentation file is rebuilt
after saving a Template or Field, which adds overhead - do not deploy this module
in production, this is a development tool only.

To make use of the generated stub classes, add an annotation to the top of
your template-file - for example, in the top of your "basic-page" template, you
would add the following:

    <?php
    
    /**
     * @var tpl\basic_page $page
     */

This should enable an IDE with static analysis to auto-complete properties
of the `$page` object, defined by the Fields used in the Template.

Because everything is a Page in ProcessWire, the built-in templates for
things like "admin", "role" and "user" will also be documented, which means
you can have IDE support for internal templates in modules, for any custom
user-fields, etc.

In addition, a special class (e.g. `tpl\any`) will be generated, documenting
all available Fields - this may be useful in situations where you have code
intended to work with all (or certain) Fields, e.g. any type of Page.


Example
-------

The output from this module looks like this:

    <?php

    /**
     * Generated by TemplateStubs module 2013-04-14 11:20:10
     * This file may be overwritten at any time.
     */

    namespace tpl;

    use Pageimages, Pageimage, PageArray, Page, Password;

    /**
     * "admin" template
     *
     * @property string $title Title
     * @property string $process The process that is executed on this page. Since this
     *                           is mostly used by ProcessWire internally, it is
     *                           recommended that you don't change the value of this
     *                           unless adding your own pages in the admin.
     */
    class admin extends Page
    {}

    /**
     * "basic-page" template
     *
     * @property string $title Title
     * @property string $headline Use this instead of the Title if a longer headline is
     *                            needed than what you want to appear in navigation.
     * @property string $summary Summary
     * @property string $body Body Content Yea
     * @property string $sidebar Sidebar
     * @property Pageimages|Pageimage[] $images Images
     */
    class basic_page extends Page
    {}

    /**
     * "permission" template
     *
     * @property string $title Title
     */
    class permission extends Page
    {}

    /**
     * "role" template
     *
     * @property PageArray|Page[] $permissions Permissions
     */
    class role extends Page
    {}

    /**
     * "user" template
     *
     * @property Password $pass Set Password
     * @property string $email E-Mail Address
     * @property PageArray|Page[] $roles User will inherit the permissions assigned to
     *                                   each role. You may assign multiple roles to a
     *                                   user. When accessing a page, the user will
     *                                   only inherit permissions from the roles that
     *                                   are also assigned to the page's template.
     */
    class user extends Page
    {}
