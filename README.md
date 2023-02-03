# gh-action-run-tc-test
gh composite action to run tc test

## usage

    - uses: "./actions/tc"
      with:
        test-name: tc-orders
        before: |
          pos-cli constants set --name ORDER_PAYMENT_LOCK_MINUTES --value 0
          pos-cli constants set --name ORDER_CANCEL_UNPAID_AFTER_X_HOURS --value 100000
        after: |
          pos-cli constants set --name ORDER_PAYMENT_LOCK_MINUTES --value 1
          pos-cli constants set --name ORDER_CANCEL_UNPAID_AFTER_X_HOURS --value 1
