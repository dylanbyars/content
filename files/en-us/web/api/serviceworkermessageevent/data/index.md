---
title: ServiceWorkerMessageEvent.data
slug: Web/API/ServiceWorkerMessageEvent/data
tags:
  - API
  - Deprecated
  - Experimental
  - Property
  - Reference
  - Service Workers
  - ServiceWorkerMessageEvent
  - data
browser-compat: api.ServiceWorkerMessageEvent.data
---
<p>{{APIRef("Service Workers API")}}{{deprecated_header}}</p>

<div class="warning">
  <p><strong>Warning:</strong> In modern browsers, this property has been deprecated.
    Service worker messages will now use the {{domxref("MessageEvent")}} interface, for
    consistency with other web messaging features.</p>
</div>

<p>The <strong><code>data</code></strong> read-only property of the
  {{domxref("ServiceWorkerMessageEvent")}} interface returns the event's data. It can be
  any data type.</p>

<h2 id="Syntax">Syntax</h2>

<pre
  class="brush: js">var myData = ServiceWorkerMessageEventInstance.data;</pre>

<h3 id="Value">Value</h3>

<p>Any data type.</p>

<h2 id="Examples">Examples</h2>

<p>When the following code is used inside the main thread to set up a message channel
  between it and a service worker for sending messages between the two, the event object
  of <code>onmessage</code> will be a <code>ServiceWorkerMessageEvent</code>.</p>

<pre class="brush: js">navigator.serviceWorker.ready.then(function(reg) {

  ...

      // set up a message channel to communicate with the SW
      var channel = new MessageChannel();
      channel.port1.onmessage = function(e) {
        console.log(e);
        handleChannelMessage(e.data);
      }

      mySW = reg.active;
      mySW.postMessage('hello', [channel.port2]);
  });</pre>

<h2 id="Browser_compatibility">Browser compatibility</h2>

<p>{{Compat}}</p>

<h2 id="See_also">See also</h2>

<ul>
  <li><a href="/en-US/docs/Web/API/Service_Worker_API/Using_Service_Workers">Using Service
      Workers</a></li>
  <li><a class="external external-icon" href="https://github.com/mdn/sw-test">Service
      workers basic code example</a></li>
  <li><a class="external external-icon"
      href="https://jakearchibald.github.io/isserviceworkerready/">Is ServiceWorker
      ready?</a></li>
  <li><a href="/en-US/docs/Web/API/Channel_Messaging_API">Channel Messaging</a></li>
</ul>