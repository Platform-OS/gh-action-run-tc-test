# gh-action-run-tc-test

 It automatically:
 - runs NPM script
 - publish a test report

## usage

    - uses: Platform-OS/gh-action-run-tc-test@0.0.7
      with:
        test-name: tc-orders
        before: |
          pos-cli constants set --name ORDER_PAYMENT_LOCK_MINUTES --value 0
          pos-cli constants set --name ORDER_CANCEL_UNPAID_AFTER_X_HOURS --value 100000
        after: |
          pos-cli constants set --name ORDER_PAYMENT_LOCK_MINUTES --value 1
          pos-cli constants set --name ORDER_CANCEL_UNPAID_AFTER_X_HOURS --value 1
          
          
### skipping action

    - uses: Platform-OS/gh-action-run-tc-test@0.0.7
      with:
        skip: true
        test-name: tc-orders
