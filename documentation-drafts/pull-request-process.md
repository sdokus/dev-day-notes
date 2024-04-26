# Pull Request Process

1. Create a Ticket on Green or Blue Triage depending on which repository the work you are doing is related. 
   - Ping the Product Manager for that team to add the ticket to the next upcoming sprint 
2. Create a new branch off the repo for the plugin you're addressing and name it following this guideline: https://docs.theeventscalendar.com/developer/git/branching/
3. Make your changes and don't forget to add a changelog: https://docs.theeventscalendar.com/developer/git/changelogs/
4. Open the PR pointing to the next upcoming release for that plugin: https://docs.google.com/spreadsheets/d/1m5xmULGTpqRAQzMG-pVT74Ub9AnSsOT87yGFz7toLTE/edit#gid=1365577016
5. Label your PR: https://docs.theeventscalendar.com/developer/git/labels/
6. When all required tests are passing, request a CR in #tec-dev channel 
7. Once you have approval, merge the changes and delete your branch 
8. On the JIRA ticket, change the status to PQA (and make sure to add testing instructions if applicable)