<html lang="en">
    <head>
        <meta charset="utf-8">
    </head>
    <body>
        <h1>Hello World</h1>
        <p>
            Hey there!
        </p>
        <p>
       <A HREF="login.html"> Login
       </A>
        </p>
    </body>
</html>

<php>
// include the AWS client library in your code
require "aws.phar";
use AwsCognitoIdentityCognitoIdentityClient;
use AwsStsStsClient;

// initialize a Cognito identity client using the factory
$identityClient = CognitoIdentityClient::factory(array(
    'region'  => 'us-east-1'
));

// call the GetId API with the required parameters
$idResp = $identityClient->getId(array(
	'AccountId' => 'YOUR_AWS_ACCOUNT_ID',
	'IdentityPoolId' => 'YOUR_COGNITO_IDENTITY_POOL_ID',
	// If you are authenticating your users through an identity
	// provider then you can set the associative array of tokens
	// in this call
	// 'Logins' => array(
	//	'graph.facebook.com' => 'your facebook session token',
	//)
));

</php>
