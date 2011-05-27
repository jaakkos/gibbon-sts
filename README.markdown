# gibbon

GibbonSTS is a simple API wrapper for interacting with [MailChimp STS API](http://apidocs.mailchimp.com/sts/1.0/) 1.0. It is forked from the wonderful [Gibbon](https://github.com/amro/gibbon)

##Installation

    $ gem install gibbon-sts
    
##Requirements

A MailChimp account and API key. You can see your API keys [here](http://admin.mailchimp.com/account/api).

##Usage

Create an instance of the API wrapper:

    gb = GibbonSTS::API.new(api_key)

Fetching data is as simple as calling API methods directly on the wrapper object. 
Check the API [documentation](http://www.mailchimp.com/api/1.3) for details.

### Fetching Campaigns

For example, to fetch your first 100 campaigns (page 0):

    campaigns = gb.campaigns({:start => 0, :limit => 100})
    
### Fetching Lists

Similarly, to fetch your first 100 lists:

    lists = gb.lists({:start => 0, :limit=> 100})
    
### More Advanced Examples

Getting batch member information for subscribers looks like this:

    info = gb.list_member_info({:id => list_id, :email_address => email_array})

or

    info = gb.listMemberInfo({:id => list_id, :email_address => email_array})
    
Fetch open and click detail for recipients of a particular campaign:

    email_stats = gb.campaign_email_stats_aim({:cid => campaign_id, :email_address => email_array})

or

    email_stats = gb.campaignEmailStatsAIM({:cid => campaign_id, :email_address => email_array})

### Other Stuff

Gibbon defaults to a 30 second timeout. You can optionally set your own timeout (in seconds) like so:

    gb.timeout = 5

##Thanks

* [Amro Mouse](https://github.com/amro)
* [Justin Ip](https://github.com/ippy04)
* [elshimone](https://github.com/elshimone)

* Rails for camelize gsub

##Copyrights

* Copyright (c) 2010 Amro Mousa. See LICENSE.txt for details.
* MailChimp (c) 2001-2010 The Rocket Science Group.