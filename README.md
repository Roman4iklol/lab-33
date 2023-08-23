<script>
	window.RLQ = window.RLQ || [];
	window.RLQ.push(function() {
		function genUID() {
			const crypto = window['crypto'] || window['msCrypto'] || false;
			if (crypto && crypto.randomUUID) {
				return crypto.randomUUID();
			} else if (crypto && crypto.getRandomValues) {
				return ([1e7]+-1e3+-4e3+-8e3+-1e11).replace(/[018]/g, function(c) {
					return (c ^ crypto.getRandomValues(new Uint8Array(1))[0] & 15 >> c / 4).toString(16);
				});
			}

			return 'xxxxxxxx-xxxx-4xxx-yxxx-xxxxxxxxxxxx'.replace(/[xy]/g, function (c) {
				const r = Math.random() * 16 | 0, v = c === 'x' ? r : (r & 0x3 | 0x8);
				return v.toString(16);
			});
		}
		function getCookie(cookieName) {
			const cookieSplit = ('; ' + document.cookie).split('; ' + cookieName + '=');
			return cookieSplit.length === 2 ? cookieSplit.pop().split(';').shift() : null;
		}
		mw.config.set({
			pvNumber: (parseInt(getCookie('pv_number'), 10) || 0) + 1,
			pvNumberGlobal: (parseInt(getCookie('pv_number_global'), 10) || 0) + 1,
			sessionId: getCookie('tracking_session_id') || genUID(),
			pvUID: genUID(),
		});
	});
</script>
