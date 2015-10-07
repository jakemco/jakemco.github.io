---
layout: default
title: Resume
group: "navigation"
permalink: /resume/
---
<div style="text-align: center; border-bottom: 1px solid #ccc; padding-bottom:10px; margin-bottom: 10px;">
<h1 style="clear:both;">Jake Maskiewicz</h1>
<strong id="tagline">Software Engineer and Security Researcher</strong>
</div>

{% include resume/publications.md %}

{% include resume/experience.md %}

{% include resume/education.md %}

<div style="float:left; width:45%; display: none;">
{% include resume/skills.md %}
</div>

<div style="float:right; width: 45%; display: none;">
{% include resume/examples.md %}
</div>

<br style="clear:both;">

<script>
$(document).on('ready', function() {
	$('.masthead').hide();
	$('.footer').hide();
	$('#microsoft').hide().next().hide().next().hide();
	$('#tagline').text('jakemaskiewicz@gmail.com - 858.229.3017 - jakemask.com');
	$('.more').hide();
});
</script>
