---
title: 'HTMLMediaElement: progress event'
slug: Web/API/HTMLMediaElement/progress_event
tags:
  - API
  - Event
  - HTMLMediaElement
  - Reference
  - Web
  - progress
browser-compat: api.HTMLMediaElement.progress_event
---
<div>{{APIRef}}</div>

<p>The <strong><code>progress</code></strong> event is fired periodically as the browser loads a resource.</p>

<table class="properties">
 <tbody>
  <tr>
   <th scope="row">Bubbles</th>
   <td>No</td>
  </tr>
  <tr>
   <th scope="row">Cancelable</th>
   <td>No</td>
  </tr>
  <tr>
   <th scope="row">Interface</th>
   <td>{{domxref("Event")}}</td>
  </tr>
  <tr>
   <th scope="row">Event handler property</th>
   <td><code>onprogress</code></td>
  </tr>
 </tbody>
</table>

<h2 id="Examples">Examples</h2>

<h3 id="Live_example">Live example</h3>

<h4 id="HTML">HTML</h4>

<pre class="brush: html">&lt;div class="example"&gt;

    &lt;button type="button"&gt;Load video&lt;/button&gt;
    &lt;video controls width="250"&gt;&lt;/video&gt;

    &lt;div class="event-log"&gt;
        &lt;label&gt;Event log:&lt;/label&gt;
        &lt;textarea readonly class="event-log-contents"&gt;&lt;/textarea&gt;
    &lt;/div&gt;

&lt;/div&gt;</pre>

<pre class="brush: css hidden">.event-log-contents {
  width: 18rem;
  height: 5rem;
  border: 1px solid black;
  margin: .2rem;
  padding: .2rem;
}

.example {
  display: grid;
  grid-template-areas:
              "button log"
              "video  log";
}

button {
  grid-area: button;
  width: 10rem;
  margin: .5rem 0;
}

video {
  grid-area: video;
}

.event-log {
  grid-area: log;
}

.event-log&gt;label {
  display: block;
}
</pre>

<h4 id="JavaScript">JavaScript</h4>

<pre class="brush: js">const loadVideo = document.querySelector('button');
const video = document.querySelector('video');
const eventLog = document.querySelector('.event-log-contents');
let source = null;

function handleEvent(event) {
    eventLog.textContent = eventLog.textContent + `${event.type}\n`;
}

video.addEventListener('loadstart', handleEvent);
video.addEventListener('progress', handleEvent);
video.addEventListener('canplay', handleEvent);
video.addEventListener('canplaythrough', handleEvent);

loadVideo.addEventListener('click', () =&gt; {

    if (source) {
        document.location.reload();
    } else {
        loadVideo.textContent = "Reset example";
        source = document.createElement('source');
        source.setAttribute('src', 'https://mdn.github.io/learning-area/html/multimedia-and-embedding/video-and-audio-content/rabbit320.mp4');
        source.setAttribute('type', 'video/mp4');

        video.appendChild(source);
    }
});</pre>

<h4 id="Result">Result</h4>

<p>{{ EmbedLiveSample('Live_example', '100%', '250px') }}</p>

<h2 id="Specifications">Specifications</h2>

{{Specifications}}

<h2 id="Browser_compatibility">Browser compatibility</h2>

<p>{{Compat}}</p>

<h2 id="See_also">See also</h2>

<ul>
 <li>{{domxref("HTMLAudioElement")}}</li>
 <li>{{domxref("HTMLVideoElement")}}</li>
 <li>{{HTMLElement("audio")}}</li>
 <li>{{HTMLElement("video")}}</li>
</ul>