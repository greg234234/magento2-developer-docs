Magento 2 Extension Model Proposal: Alpha 1
===========================================

As part of the overall push in Magento 2 for better modularity, we're
introducing support for a few new ideas in the recent push to the Github
repository.   A major theme of these changes is the separation of
responsibilities, primarily between business logic on one side and presentation
logic and user experience on the other.

![](</images/archExtensibility.png>)

The diagram above attempts to describe the ideas behind these changes visually. The source code for the proposed changes can be found in the recent github push [here][1]. There is also a VirtualBox image that contains the installation of recent Magento-2 code base [here][2]. The instructions for using the virtualbox image can be found [here][3]

[1]: <https://github.com/magento/magento2>
[2]: <https://ebay.box.com/s/a2k6twcsoappu4zv5lsq>
[3]: <http://praveenck.github.io/docs/vmimage/>

Services
--------

Services provide a single, common entry point for all interaction between different UIs,
including Blocks, Controllers and web services; and it can even serve as an
interface for business logic for other modules.

Services have well defined interfaces described using a service IDL. Service IDL
documents the list of public methods available to templates, blocks, controllers
and web services. For each method, the input and output data types are defined
using XSDs.

Webhooks and Callbacks
----------------------

As a nod to the desire to support better remote integrations with Magento, as
well, we're not only working on automatically exposing these Services as web
services to external clients, but with this release, we're also introducing
support for real-time integrations with remote system using webhooks and
callbacks.

Webhooks provide Event Observer-like behavior over HTTP and allow you to be
notified when certain events occur with Magento and even get real-time data from
the system.  Callbacks also support communication from your Magento installation
out to a remote system, but callbacks trigger synchronously and use the response
from the remote integration in the rest of the user request processing.  As an
example, in this release we're supporting the ability to define remote shipping
carriers where the shipping rates and retrieved over an HTTP call.

Better Templating
-----------------

On the presentation tier, we're introducing support for Twig templating.  Theme
development has always been a big part of Magento store customization, but
templates written in PHP meant that business logic occasionally was written into
the .phtml files.  This meant that the business logic was either lost or had to
be duplicated from theme to theme.  With a templating language like Twig, which
uses a restricted syntax, it is easier to ensure that your template files will
only be concerned with the logic needed to render your data.

Since templates need data to render and Services are designed to provide a
well-managed, consistent view of the data a module can provide, we've introduced
a syntax for binding templates to a service call directly from the layout file.

Extension Configuration Improvement
-----------------------------------

There's another small improvement that we've made to System Configuration that
we hope will make your life a little easier.  For most of the configuration
fields you define, you can describe everything you need in XML -- except for the
values of a select box.  We've introduced a syntax with this push that will
allow you to describe static select options inline, and dynamic options can be
extracted from the result of a service call.

These concepts have been introduced in isolated parts of the Magento application
so far in the hopes that you will comment on their value and help direct and
refine how they work.  This is the first set of many ideas that we're looking at
to help improve the modularity of Magento, which should improve not only the
compatibility of extensions within Magento, but also the upgradability of
Magento itself.

New Approach for Creating Extensions/Customizations
-----------------------------------------------

Here's an outline of how to create an extension that includes some business logic and associated presentation logic:

-   Create a service that encapsulates the extensions business logic. As part of the service creation, define the service interface using the service IDL. List all methods whose output is need in the presentation tier. Define the method input and output using XSDs

-   Create a template that renders the visual aspects

-   Associate the template's reuired data to one or more service calls via configuration in layout.xml

-   Optionally, accept configuration for your extension using option lists.
