<html>

<head>
    <script type="text/javascript" src="https://ajax.googleapis.com/ajax/libs/jquery/2.1.0/jquery.min.js"></script>

    <style>
        body {
            font-family: Roboto, sans-serif;
            background: #f1f1f1;
        }

        table,
        th,
        td {
            border: 1px solid black;
            border-collapse: collapse;
        }

        th,
        td {
            padding: 5px;
            text-align: left;
        }
    </style>
</head>

<body onload="getAuthCode();">
    <script type="text/javascript">

        var authCode = getParameterByName('code');
        var errorCode = getParameterByName('error');
        var responseState = getParameterByName('state');
        var errorDescroption = getParameterByName('error_description');
        postPayload =
            "grant_type=authorization_code\n" +
            "&client_id=" + window.opener.client_id + "\n" +
            "&redirect_uri=" + window.opener.redirect_uri + "\n" +
            "&code=" + authCode


        function getAuthCode() {
            getErrorCode(errorCode)
            window.opener.authorization_code = authCode;
            $(".authCode", window.opener.document).text(authCode);
            $("#responseState", window.opener.document).text(responseState);
            $("#tokenPostPayload", window.opener.document).text(postPayload);

        }

        function getErrorCode(err) {
            if (err != "") {
                alert(error_description)
                return
            }
        }

        function getParameterByName(name) {
            name = name.replace(/[\[]/, "\\[").replace(/[\]]/, "\\]");
            var regex = new RegExp("[\\?&]" + name + "=([^&#]*)"),
                results = regex.exec(location.search);
            return results === null ? "" : decodeURIComponent(results[1].replace(/\+/g, " "));
        }




    </script>
    <h2> Launch URL Authorization Successful.</h2>
    (You can close this window. We'll add the state and authorization code in the address bar of this window to the
    tables on the previous screen.)
</body>

</html>
