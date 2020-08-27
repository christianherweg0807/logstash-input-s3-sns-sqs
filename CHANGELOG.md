##2.1.1
- FEATURE: Enable Multiregion Support for included S3 client.
- Add region by bucket feature
##2.1.0
- FEATURE: Add S3 metadata -> config :include_object_properties
- FEATURE: Watch for threads in exception state and restart...
##2.0.9
-gzip dectection should return false for files smaller than gzip_signiture_bytes
##2.0.8
-fix nil class error
##2.0.7
-fix gem error
##2.0.6
-fix: fix crash of extender
##2.0.5
-fix: crash on 0 byte file
-fix: type by folder function
##2.0.4
-fix: type-by-folder repair
-fix: crash on 0 byte file
##2.0.3
- Increase max parsing time -> drop event if reached
- watcher thread should raise an error in poller loop if timeout reached.
- remove some debug logs

##2.0.2
FIX:
- Terminate every input line by \n (BufferedReader does not)
- Wrong input for type folder, leads to empty types
##2.0.1
FIX:
- Deadlock while message decoding
- make method stop? public

##2.0.0
Breaking Changes:
- s3_key_prefix was never functional and will be removed. Actually only used for metadata.folder backward compatibility.
  config for s3 paths are regex (if not exact match)
- s3_options_by_bucket substitutes all s3_* options
  We will merge deprecated options into the new structure for one release
Changes:
- Refactor plugin structure to be more modular 
- Rework threadding design
- introduce s3_options_by_bucket to configure settings (e.g aws_options_hash or type)
##1.6.1
- Fix typo in gzip error logging
##1.6.0
- add a test to tmp file deletion
- revert type folder regex
##1.5.9
- Fix regex for type folder
##1.5.8
- Add some debug and a toggle for delete
##1.5.7
- Remove Debug poutput
##1.5.6
-BugFix
##1.5.5
- Memo to me: better testing :-) Fix msg -> message
##1.5.4
- BugFix
##1.5.3
- Try to fix requeue Problem
## 1.5.2
- BugFix Set Metadata bucket,key,folder
- Feature: Possibility to fall back to old threadding model by unset consumer_threads
## 1.5.1
- BugFix: rescue all AWS::S3 errors
## 1.5.0
- Feature: Use own magicbyte detector (small&fast)
## 1.4.9
- Feature: Detect filetype with MagicByte 
## 1.4.8
- Bufix: CF Metadata events Bug #7
- Feature: use aws-role for s3 client connection.
## 1.4.7
Remove from rubygems.org
## 1.4.6
- BugFix: jRuby > 2 : No return from block
- BugFix: No exit on gzip error
## 1.4.5
- BugFix: undeclared var in rescue 
## 1.4.4
- Feature: make set_codec_by_folder match as regex
  e.g.: set_codec_by_folder => { ".*-ELB-logs" => "plain"} 
## 1.4.3
- Fix: skip_delete on S3::Errors::AccessDenied
- Feature: codec per s3 folder
- Feature: Alpha phase: different credentials for s3 / default credentials for sqs
- Feature: Find files folder. 
## 1.4.2
- Fix: Thread shutdown method should kill in case of wakeup fails
## 1.4.1
- Fix: Last event in file not decorated
- Adjust metadata namings
- Event decoration in private method now.
## 1.4.0
- Filehandling rewritten THX to logstash-input-s3 for inspiration
- Improve performance of gzip decoding by 10x by using Java's Zlib
- Added multithreading via config Use: consumer_threads in config
## 1.2.0
- Add codec suggestion by content-type
- enrich metadata 
- Fix some bugs
## 1.1.9
- Add config for s3 folder prefix, auto codec and auto type
## 1.1.8
- Add config switch for delivery with or without SNS
## 1.1.6
- Fix a nil exception in message parsing
## 1.1.5
- Fix loglevel for some debug messages
## 1.1.4
- Add Account-ID to config
## 1.1.2
- Fix a Bug in the S3 Key generation
- Enable shipping throug SNS Topic (needs another toJSON)
## 1.1.1
- Added the ability to remove objects from S3 after processing.
- Workaround an issue with the Ruby autoload that causes "uninitialized constant `Aws::Client::Errors`" errors.

## 1.1.0
- Logstash 5 compatibility

## 1.0.3
- added some metadata to the event (bucket and object name as commited by joshuaspence)
- also try to unzip files ending with ".gz" (ALB logs are zipped but not marked with proper Content-Encoding)

## 1.0.2
- fix for broken UTF-8 (so we won't lose a whole s3 log file because of a single invalid line, ruby's split will die on those)

## 1.0.1
- same (because of screwed up rubygems.org release)

## 1.0.0
- Initial Release
