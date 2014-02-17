UPDATE xf_user_authenticate
SET data = BINARY
	CONCAT(
		CONCAT(
			CONCAT('a:3:{s:4:"hash";s:40:"', SHA1(CONCAT(SHA1('new-password'), SHA1('salt')))),
			CONCAT('";s:4:"salt";s:40:"', SHA1('salt'))
		),
		'";s:8:"hashFunc";s:4:"sha1";}'
	),
scheme_class = 'XenForo_Authentication_Core'
WHERE user_id = 1;
