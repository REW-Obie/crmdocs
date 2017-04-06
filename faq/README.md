# FAQ

Jump to:

- [Leads](#leads)
- [Teams](#teams)

## Leads

- Q. How to recover a deleted lead?
  - ...

- Q. How would you set up text messages? Do you have to contact support to add your number so that you can send out text messages?
  - Yes, you need to configure each beta site to work with the "REW Twilio" API. The tool to do this is here: http://twilio.rewhosting.com/
  - Instructions:
    - Obtain REW API key by logging into the REW backend and navigate to: Leads > Tools > API Settings
    - Go here and "Add New Account" using API key from previous step 1: http://twilio.rewhosting.com/
    - Update the `modules.yml` to use the REW Twilio API key from step 2: `REW_PARTNERS_TWILIO: abc123xyz`
      - <a href="https://git.rewhosting.com/enterprise/deploy/blob/dev/config/environments/4.8-bcse/modules.yml#L43">https://git.rewhosting.com/enterprise/deploy/blob/dev/config/environments/4.8-bcse/modules.yml#L41</a>

## Teams

- Q. Should there be a rule on how many leads a member should take a day?
  - ...

- Q. What if a team member decides to take all or most of the leads?
  - ...