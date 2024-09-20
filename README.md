# django_page_maker
Create web pages for models in django automatically base on a descriptor.

For Example : 
I have a model its name is : book
I wanna create <manager(list of books with pagination and create filter box for its fields)>,<add>,<edit>,<delete>

So I only need to create a descriptor.py file such as :

descriptor.py
  from django.conf import settings
  
  LIST_PAGE = settings.LIST_PAGE_TEMPLATE
  book_drcp = {
      'model_app': 'app_db',
      'model': 'book',
      'list_extend': LIST_PAGE,
      'page_title': 'Book Manager',
      'order_by': "-id",
  }

And add these urls to my url files.

path('book/manager', ListPage.as_view(dcrp=book_drcp), name='book_manager'),
path('book/add', AddPage.as_view(dcrp=book_drcp), name='book_add'),
path('book/update/<pk>', UpdatePage.as_view(dcrp=book_drcp), name='book_update'),
path('book/delete/<pk>', DeletePage.as_view(dcrp=book_drcp), name='book_delete'),



This module help us to develop our websites as soon as possible.
