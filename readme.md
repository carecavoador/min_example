# Issue when trying to use transformations with PyPDF2.

I'm currently working on a minimal application to merge several PDF files in a single big PDF page file. Sometimes I need to rotate it too.

To do so, I'm currently using the `mergeTranslatedPage` method of the `PageObject` class. But, it says it's deprecated and I should use `add_transformation` and `merge_page` instead.

When I try to use the `add_transformation` method:

```python
# lines 32 to 35 of 'example.py'
op = Transformation().translate(tx=last_x, ty=0)
page_to_merge.add_transformation(op)
new_page.merge_page(page_to_merge, expand=True)
```

The result is not what I was expecting:
![Unexpected behavior](images/merged_not_ok.png)

But if I look at the wireframe I can see something happens. I suspect the translation is occuring on the page objects, but not on the trimbox:

![Wireframe view](images/merged_not_ok_wf.png)

Although the `mergeTranslatedPage` method works as intended:

![Expected behavior](images/merged_ok.png)

So, what's the big deal? Why don't I just use `mergeTranslatedPage` then?

Well, if I need to rotate some page before merging it to the big page, I never get the desired result whatever the method I use, be it `mergeRotatedTranslatedPage` or using the `translate` and `rotate` methods on the `Transformation` object.

I appreciate your attention and any insights will be very really kind. Thank you!
