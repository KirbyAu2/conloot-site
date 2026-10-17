---
layout: page
title: Unsubscribe
permalink: /unsubscribe/
sitemap: false
robots: noindex
---

# Unsubscribe from ConLoot™ emails

One more tap. Confirming stops newsletters and convention recaps to this
address. Account emails — password resets, vendor application and approval
mail — only go out when you ask for them and are not affected.

<form id="unsub" method="post" action="https://akfsqmyvgyatkxwyjwgs.supabase.co/functions/v1/unsubscribe" style="margin:24px 0">
  <input type="hidden" name="confirm" value="1">
  <button type="submit" id="unsub-btn" style="font:inherit;font-weight:500;padding:12px 20px;border:1px solid #D9A93D;border-radius:6px;background:#D9A93D;color:#0E1014;cursor:pointer">Yes, unsubscribe me</button>
</form>
<p id="unsub-missing" hidden>This link is missing its token — it may have been cut off by your mail app. Open the original email and tap the unsubscribe link again, or reply to it with "unsubscribe" and we'll take care of it.</p>

<script>
  (function () {
    // The footer link carries ?t=<signed token>; the Edge Function redirects a
    // GET here (it never writes on GET — mail scanners follow GET links). The
    // token goes back on the form's action; the body just marks this as a
    // browser confirm rather than an RFC 8058 one-click POST.
    var t = new URLSearchParams(location.search).get('t');
    var form = document.getElementById('unsub');
    if (t && /^[A-Za-z0-9_-]{1,1024}$/.test(t)) {
      form.action += '?t=' + encodeURIComponent(t);
    } else {
      form.hidden = true;
      document.getElementById('unsub-missing').hidden = false;
    }
  })();
</script>

Changed your mind later? Reply to any ConLoot email and we'll add you back.
Questions: [conlootapp@gmail.com](mailto:conlootapp@gmail.com).
