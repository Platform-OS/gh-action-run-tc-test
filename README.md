# gh-action-run-tc-test

 It automatically:
 - runs NPM script
 - publish a test report
 
 the report will be published under the $UPLOAD_HOST/$REPORT_PATH-`test-name` URL, so these two environment variables are required. See usage for details.

## usage

    tests:
      env:
        REPORT_PATH: ${{ needs.reserve-ci-instance.outputs.report-path }}
        UPLOAD_HOST: https://tests.qa0.oregon.platformos.com
      
      steps:
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
