<?php

// example: https://github.com/onlinetuts/line-bot-api/blob/master/php/example/chapter-01.php

include ('line-bot-api/php/line-bot.php');

$channelSecret = 'e327e98bf20d9d5fae714e4a51e27697';
$access_token ='GlxpHTGJf86xMl2lPNrtpen2aFkfk7vP7TPAqBEW7dUXWhV4YQtXvk1F1+HDcJ9r1MtXHG5SqoxuWXz7nKq5jWCFNIo4bpnjccw9g4kr3O7EyL7hPNJCL+WcDSLtbAtaouxGFf6pcP5FnQpgjYhQgAdB04t89/1O/w1cDnyilFU=';

$bot = new BOT_API($channelSecret, $access_token);
	
if (!empty($bot->isEvents)) {
		
	$bot->replyMessageNew($bot->replyToken, json_encode($bot->message));

	if ($bot->isSuccess()) {
		echo 'Succeeded!';
		exit();
	}

	// Failed
	echo $bot->response->getHTTPStatus . ' ' . $bot->response->getRawBody(); 
	exit();

}
