# liensutils
# creer une cerriver linux sur windows 10 et installer kali lunux unbutu et debian

## deploi django

https://www.digitalocean.com/community/tutorials/how-to-serve-django-applications-with-apache-and-mod_wsgi-on-ubuntu-16-04


## redis sur windos 10
https://redislabs.com/blog/redis-on-windows-10/

## Django channels

https://channels.readthedocs.io/en/latest/tutorial/part_2.html



## Django requierement.txt file

```bash
pip freeze
pip freeze > requirements.txt

pg_dump -U postgres reveci > reveci.pgsql
```


https://medium.com/python-pandemonium/better-python-dependency-and-package-management-b5d8ea29dff1



# Intall Redis Mac OS

https://1upnote.me/post/2018/06/install-config-redis-on-mac-homebrew/


# Chat python 3 redis postgres

https://revs.runtime-revolution.com/a-simple-real-time-chat-with-django-channels-and-react-b73edc3a79f2



# Lien console code pen
https://codepen.io/nullobject/pen/cngzI


# Lien extended user models Django use  option 2

https://simpleisbetterthancomplex.com/tutorial/2016/07/22/how-to-extend-django-user-model.html

## Ifram vue js 

https://dev.to/pulljosh/how-to-load-html-css-and-js-code-into-an-iframe-2blc


## Django admin

https://github.com/alesdotio/django-admin-shortcuts


pip install django-rest-swagger

https://www.django-rest-framework.org/api-guide/serializers/#dealing-with-nested-objects


## CREATE DB POSTGRES

https://www.guru99.com/postgresql-create-database.html


## template fouter

HTTPS://startflutter.com


https://www.travelpayouts.com/finance/requisites


https://colorlib.com/wp/cat/event/

http://www.travelpayouts.com/developers/api


## Django QR code

https://django-qr-code.readthedocs.io/en/latest/pages/README.html


## Django generate admin


https://django-admin-generator.readthedocs.io/en/latest/usage.html#usage



https://undraw.co/

## Django import export for import xls csv etc...

https://django-import-export.readthedocs.io/en/latest/

## Django sessions management

https://pypi.org/project/django-user-sessions/

https://django-user-sessions.readthedocs.io/en/stable/installation.html

## Date picker
http://www.daterangepicker.com/

## Map

https://developer.mapquest.com/plan_purchase/steps/business_edition/business_edition_free/register

https://business.mapquest.com/pricing-plans/

https://www.bingmapsportal.com/ManageDataSources#/

https://docs.traveltimeplatform.com/overview/getting-keys

https://www.openstreetmap.org/traces

https://openrouteservice.org/dev/#/home

## Django rest Framework

https://books.agiliq.com/projects/django-api-polls-tutorial/en/latest/

## WEB RADIO PLAYER

https://medium.com/crowdbotics/build-your-own-radio-streaming-app-with-howler-js-637f929decc0



## . https://api.youtubeplaylist.cc/playlist?url=https%3A%2F%2Fwww.youtube.com%2Fwatch%3Fv%3DzQOrahE-0Cs%26list%3DPLi-5xFHLno9qigE6CuCFB31zrinpdE_ZN&nextPageToken=



https://realpython.com/python-speech-recognition/





##Django transfert data


https://www.shubhamdipt.com/blog/django-transfer-data-from-sqlite-to-another-database/
https://djangopackages.org/grids/g/django-rest-framework/





https://swup.js.org/getting-started/reloading-javascript


https://bosnadev.com/2015/12/15/allow-remote-connections-postgresql-database-server/



## Custom popup field
forms.py
```python
class OrderNewForm(forms.ModelForm):

   client = forms.ModelChoiceField(
       required=False,
       queryset=Client.objects.all(),
       widget=RelatedFieldWidgetCanAdd(Client, related_url="so_client_add")
                                )
   class Meta:
       model = Order
       fields = ('code', 'client')
 ```
 
And the widget, that renders the "+" button and link to the add popup in the admin interface or to a custom view you provice with the related_url argument is:

```python

from django.core.urlresolvers import reverse
from django.utils.safestring import mark_safe
from django.forms import widgets
from django.conf import settings

class RelatedFieldWidgetCanAdd(widgets.Select):

    def __init__(self, related_model, related_url=None, *args, **kw):

        super(RelatedFieldWidgetCanAdd, self).__init__(*args, **kw)

        if not related_url:
            rel_to = related_model
            info = (rel_to._meta.app_label, rel_to._meta.object_name.lower())
            related_url = 'admin:%s_%s_add' % info

        # Be careful that here "reverse" is not allowed
        self.related_url = related_url

    def render(self, name, value, *args, **kwargs):
        self.related_url = reverse(self.related_url)
        output = [super(RelatedFieldWidgetCanAdd, self).render(name, value, *args, **kwargs)]
        output.append(u'<a href="%s" class="add-another" id="add_id_%s" onclick="return showAddAnotherPopup(this);"> ' % \
            (self.related_url, name))
        output.append(u'<img src="%sadmin/img/icon_addlink.gif" width="10" height="10" alt="%s"/></a>' % (settings.STATIC_URL, _('Add Another')))                                                                                                                               
       return mark_safe(u''.join(output))
```
