<script>
	export let tracker;

	function getQueryStringValue (parameter) {
	    var currentPageURL = window.location.search.substring(1);
	    var queryString = currentPageURL.split('&');
	    var getParameter;
	    var i;
	    for (i = 0; i < queryString.length; i++) {
	        getParameter = queryString[i].split('=');
	        if (getParameter[0] === parameter) {
	            return getParameter[1] === undefined ? true : decodeURIComponent(getParameter[1]);
	        }
	    }
	};

	let url_tracker = getQueryStringValue("t");

	if (url_tracker != undefined) {
		localStorage.setItem("t", url_tracker);
		tracker = url_tracker;
	} else {
		console.log("using local storage");
		tracker = localStorage.getItem("t");
	}

	if (localStorage.getItem("t") == null) {
		localStorage.setItem("t", "");
		tracker = "";
	}

	//tracker = localStorage.getItem("t");
</script>