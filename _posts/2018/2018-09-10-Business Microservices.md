---
layout: page
subheadline: 
title:  "Business Microservices"
teaser: "Business microservices are a powerful technique to use for building integrations."
meta_teaser: "meta teaser"
breadcrumb: false
categories:
    - architecture
    - integration
tags:
    - blog
    - content
    - post
    - post format
header: no
image:
    title: gallery-example-1.jpg
    caption: Unsplash.com
    caption_url: http://unsplash.com
author: eddiebrady
---

What we do
Organized Bits builds business microservices.  The microservices are all integrated using OpenID Connect.  In our case we&apos;re using Identity Server 4.  A few points regarding the microservices.

1)	The business microservices can achieve SSO by implementing OpenID Connect.
2)	The business microservice APIs can be secured using OAuth 2.  APIs create a public facing abstraction layer for the Organization which allows them to communicate with 3rd party partners in secure way.  That security governed and controlled by the Organization itself.  It is where the Organizations business logic resides.  Further, this abstraction layer decouples 3rd party integrations from the internal systems that operate the business.  This decoupling is important as it allows an Organization to remain agile.
3)	Our business microservice user interfaces can be seamlessly, visually integrated into the iMIS UI (courtesy of OpenID Connect).  Interestingly, it turns out that Shopify is doing something similar to what we�re doing but they have a proprietary way of achieving SSO instead of using OpenID Connect.  In this regard, our approach is more modern.  As they have been around for a while I assume they built their approach prior to OpenID Connect being the standard.  Shopify was founded 2004.  OpenID Connect spec completed 2014.

So what are the benefits?

Benefits of Microservices
                Decoupling
                Small, agile development and deployment
                Performance
                Scalability
                Use of the latest technologies
                Each microservice can use the technologies that are most appropriate for its use case

Benefits of OpenID Connect
                Industry standard protocol. 
                                It&apos;s built by security experts to be a secure protocol, as opposed to a �custom built, proprietary protocol� built by non-security experts.
Many systems already use OpenID Connect (Drupal, WordPress, Dynamics CRM, etc�) and these systems become plug and play.  Conversly, a custom protocol would require custom programming to integrate all applications together.
                                I have been told by the iMIS product owners that ASI has OpenID Connect support on their roadmap in order to provide a better integration story.  We&apos;re ahead of them.

                Connecting OpenID Connect applications via SSO becomes a matter of registering the application in Identity Server.  It is simply a �registration process�.

OpenID Connect Authentication servers become swappable without affecting client applications.  You can swap one authentication provider for another since both implement the same protocol and since the applications are programmed against the protocol itself, they remain blissfully unaware of the specific authentication server.  You can start with Identity Server and later switch to Auth0 or some other hosted service.  There are many options and because they all implement the same protocol they are interchangeable.

Identity Server 4
                Implements the OpenID Connect standard
                Provides SSO via OpenID Connect
                Is used to secure custom API�s via OAuth 2
                Is backed by the .NET Foundation
                Is OpenID Connect certified
                Has a growing number of experts that understand this technology (as opposed to a custom, proprietary system that is understood by only a single company).  There is free and commercial support.

                Centralized security - Authentication as a service.  Applications themselves do not need to implement this concern over and over again in each application.
                Consistent branding and user familiarity.  There is a single recognizable login screen presented to your users.  Whether they are logging in via mobile, desktop, or web application.
                Integrates easily with other �external providers� such as Facebook, linked in, google, etc.
                Single Sign-on / Sign-out
                Access Control for APIs
                Customizable

Our Interpretation
Ultimately, an organization cares about only 3 things:
1)	Their users and data
2)	Their business processes
3)	Security

Hardware and software are a means to an end.  An Organization only cares about hardware and software to the extent that it enables them to collect and process their data in a secure way.  PERIOD!

Hardware has evolved to the point where it is now a commodity, available at your fingertips.  The cloud is awesome.

Software has a ways to go but we&apos;re moving in the right direction.  One day, I think soon, software will become a plug and play commodity as well, where integration happen automatically as a result of standard protocols.  We�ve seen software development go from everything needing to be custom built to a point where there are mature products like CRMs and CMSs that can achieve so much without any programming at all.  We&apos;re now in an era where the need is more to integrate systems rather than build them from scratch.  Of course, there is still a need at times for custom software but that need is becoming less and less as SaaS applications mature and proliferate.  Most of the time it is better to go SaaS than custom built.  

So the need now is not custom software development but instead integration.  So when we start looking at integration then we start looking at standard protocols.  For instance, OpenID Connect allows systems to achieve SSO by a simple registration process.  Business logic is exposed between systems via APIs  using REST or GraphQL and secured by OAuth 2.

An organization should be able to swap one service for another with as little friction as possible.  Integrations are not yet automatic but that is the vision that we are striving for.

CRM � iMIS, Salesforce, Dynamics
CMS � iMIS, Drupal, WordPress, etc�
Store � iMIS, Shopify, Magento
Event Registration � iMIS, Eshow
Donation Services � iMIS, etc�
Forms � WuForms, etc..
Surveys services � survey monkey, etc�

An organization has many business processes.  The challenge is to select which software products best serve the organizations needs, and do so in a way that does not tightly couple the organization to any particular product.  An organization needs to remain as agile as possible.  There are so many services to choose from.

On premise installation of commercial products
Cloud hosted SaaS services
Custom built services
Open Source products

The solution to these challenges lies in OpenID Connect and microservices!

{% highlight ruby linenos %}
def foo
  puts 'foo'
end
{% endhighlight %}

{% highlight csharp %}

public string testfunction()
{
    var test = "test";
}
{% endhighlight %}
