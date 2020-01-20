---
layout: post
title:      "Javascript / Rails Project "
date:       2020-01-20 05:37:44 +0000
permalink:  javascript_rails_project
---


I wasn't prepared for the amount of work that would go into this project. I finished my last weeks course work a couple days early and decided to start on the project a couple of days before it was technically assigned, I'm glad I did. 
For this project I decided to make an instagram clone geared towards my favorite hobby, Fishing. My inital idea was to add parameters to the uploaded post to allow it to be sorted by the weight of the fish caught, and lure used. I started going down the rabbit hole quick with this and decided to just stick to the project requirements first and then if I had time in the end add more features. So, I started with a user being able to create a post with an image, a caption, and a couple of other parameters. I also added the ability to be able to create comments under the post. 

My first problem was figuring out how to submit an image from the front end with a form and send it to the backend. The way I planned to do it didn't have many resources on the subject. Most suggested to upload it to a file upload resource like AWS S3, but I didn't like the idea of having the front end handle anything with files. By piecing a couple of blog posts together I found out that you can create a FormData() object in JS and append the image and other input values from the form. For some reason it doesn't allow you to pass the form directly as an argument, so you have to manually append every form item to the FormData object. Here's an example. 

```
createPost(formValues) {
		const post = new FormData();
		post.append('image', valuesToAppend.image);
		post.append('caption', valuesToAppend.caption);

		
		return fetch(this.baseUrl, {
			method: 'POST',
			body: post
		}).then(res => res.json());
	}
```

You may be wondering where the 'Content-Type' is, it's not needed! The FormData object automatically sends it via the 'Content-Type' multipart/form-data. This allows not just images but other files to be sent via a fetch request. On the backend I set up to recieve the file via Active Storage. Just install active storage, set the model to 'has_one :attached', set your incoming params to accept your image and Active Storage will take care of the rest of the storage. 

Getting the image file back the front end was another speed bump. You can't send the image file itself, you send the url of the image that's stored locally on your machine. In order to do this I created an instance method within the model and used url_helpers to grab the url of the file. Example

```
include Rails.application.routes.url_helpers

class Post < ApplicationRecord
  has_many :comments, dependent: :destroy
  has_one_attached :image, dependent: :destroy
  
  def image_url
    url_for(self.image)
  end

end
```

Now I can call that method on the instance of post when I render my JSON response and send the image url. I ran into a problem where the image wasn't displaying and was throwing an implicit conversion error, I had to rollback Rack to an earlier version and it worked fine.  I learned alot from this project, I had alot more problem solving to do on this one which was welcome as that's what lures me into this field. Becoming more organized with my javascript code is my next goal, I felt like it was alot harder in Javascript to keep things organized than rails. Can't wait for React! Peace!
