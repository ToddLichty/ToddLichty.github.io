---
layout: post
title: Open edX - Show Course Updates on Course Home Page
permalink: /open-edx-show-course-updates-on-course-home-page/
author: Todd Lichty
---
<p>With the migration to the Hawthorn release, it was decided that course updates would no longer show on the course outline page. Why this decision was made, I will never understand. Student's are NOT going to click the Updates link every time they browse the course outline page just to check if there are new updates to the course. I found a discussion about this here: <a href="https://discuss.openedx.org/t/course-updates-converted-to-welcome-message-with-no-replacement-ouch/226">https://discuss.openedx.org/t/course-updates-converted-to-welcome-message-with-no-replacement-ouch/226</a></p><p>Looking through the source code, I was able to find a waffle flag that allows me to override this setting:</p><!--kg-card-begin: markdown--><pre><code>if LATEST_UPDATE_FLAG.is_enabled(course_key):
                update_message_fragment = LatestUpdateFragmentView().render_to_fragment(
                    request, course_id=course_id, **kwargs
                )
</code></pre>
<!--kg-card-end: markdown-->
<p>So, the functionality is still in the Ironwood release, it is just disabled by default. Again, I have NO IDEA why this would be the case. To override this setting, you can add a flag override this.</p><ol><li>Go to the Django admin site and click on Waffle flag course overrides under the Waffle_Utils section.</li><li>Enter course_experience.latest_update in the Waffle Flag field.</li><li>Enter the course ID in the Course ID field. (i.e. course-v1:UofW+CS115+2020_09).</li><li>Select Force On from the Override Choice drop down.</li></ol><p>Saving this setting will turn on the latest course updates on the course outline page.</p><figure class="kg-card kg-image-card"><img src="/images/openedx_course_updates_latest_update.png" class="kg-image"></figure>