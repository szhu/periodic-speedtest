periodic-speedtest
==================

I don't think my ISP's that great, but I need some proof. This LaunchAgent does
a speed test every 15 minutes.

How much bandwidth does this thing use?

      30 MB/test
       4 tests/hour
      24 hours/day
    × 30 days/month
    ———————————————
      86 GB/month

I have a 250GB/month cap that I never get close to, and I don't plan on running
this permanently, so I figure it's fine.

Requirements
------------

- Mac OS
- [speedtest-cli]: `pip install speedtest-cli`

[speedtest-cli]: https://github.com/sivel/speedtest-cli

Install
-------

```sh
LA=~/Library/LaunchAgents/com.interestinglythere.periodicSpeedTest.plist
launchctl unload $LA &> /dev/null  # unload old copy, if it exists
curl -fsSL https://git.io/vTGyv > $LA
launchctl load $LA
```

Inspecting Results
------------------

- `cat ~/Library/Logs/com.interestinglythere.periodicSpeedTest.out`
- `caffeinate tail -f ~/Library/Logs/com.interestinglythere.periodicSpeedTest.out`
- `grep 'Hosted by' ~/Library/Logs/com.interestinglythere.periodicSpeedTest.out`
- `grep 'Download:' ~/Library/Logs/com.interestinglythere.periodicSpeedTest.out`
- `grep 'Upload:' ~/Library/Logs/com.interestinglythere.periodicSpeedTest.out`
