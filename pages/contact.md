---
title: Contact us
created: 2016-07-12T18:19:18+05:30
author: ashishdoneriya
permalink: /contact
updated: 2021-02-27T02:42:00+05:30
---

<style>
input, textarea {
  width: 100%;
  padding: 12px 20px;
  margin: 8px 0;
  display: inline-block;
  border: 1px solid #ccc;
  border-radius: 4px;
  box-sizing: border-box;
}

button {
  width: 100%;
  background-color: #4CAF50;
  color: white;
  padding: 14px 20px;
  margin: 8px 0;
  border: none;
  border-radius: 4px;
  cursor: pointer;
}

button:hover {
  background-color: #45a049;
}

div {
  border-radius: 5px;
  background-color: #f2f2f2;
  padding: 20px;
}
</style>
<script src="https://cdn.jsdelivr.net/npm/vue"></script>
<div id="vapp">
	<form id="contactForm" v-if="displayForm">
		<label for="name">Name</label>
		<input type="text" id="name" name="name" v-model="name" placeholder="Your name..">
		<label for="email">Email</label>
		<input type="email" id="email" name="email" placeholder="Your email.." v-model="email">
		<label for="message">Message</label>
		<textarea id="message" v-model="message"></textarea>
		<button @click="sendMessage()">Send Message</button>
	</form>
	<p v-if="!displayForm">Your message has been sent successfully</p>
</div>

<script>
		new Vue({
			el : "#vapp",
			data : {
				displayForm: true,
				name: '',
				email: '',
				message: ''
			},
			methods: {
				sendMessage() {
					var form = document.getElementById("contactForm");
					var xhr = new XMLHttpRequest();
					xhr.open(method, 'https://formspree.io/f/xknploqg');
					xhr.setRequestHeader("Accept", "application/json");
					xhr.onreadystatechange = () =>{
						if (xhr.readyState !== XMLHttpRequest.DONE)
							return;
						if (xhr.status === 200) {
							this.displayForm = false;
						} else {
							alert(xhr.response);
						}
					};
					xhr.send(data);
				}
			}
		});
	</script>