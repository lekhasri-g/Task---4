Firewall Configuration Task (Task 4)

Objective

Setup and use a firewall on Windows to allow or block traffic on
specific ports.

------------------------------------------------------------------------

Steps Performed (Windows Firewall)

1.  Opened Windows Firewall with Advanced Security by pressing Win + R,
    typing wf.msc, and pressing Enter.
2.  Selected Inbound Rules → clicked New Rule….
3.  Chose Port as the rule type.
4.  Selected TCP and specified Port 23.
5.  Action: Selected Block the connection.
6.  Applied to Domain, Private, Public profiles.
7.  Named the rule Block Telnet (port 23) and saved.

------------------------------------------------------------------------

Testing the Rule

-   Used PowerShell:

        Test-NetConnection -ComputerName localhost -Port 23

    Result: TcpTestSucceeded : False (connection blocked).

-   Optional Telnet test:

        telnet localhost 23

    Result: Could not open connection (blocked).

------------------------------------------------------------------------

Removing or Disabling the Rule

-   Go back to Inbound Rules, right-click Block Telnet (port 23), then
    choose Disable Rule or Delete.

-   Alternatively, using Command Prompt (Admin):

        netsh advfirewall firewall delete rule name="Block Telnet (port 23)" protocol=TCP localport=23 dir=in

------------------------------------------------------------------------

Notes

-   Ensure you allow important ports (like SSH or RDP) before applying
    firewall blocks on a remote machine.
-   Screenshots were taken of rule creation, the inbound rules list, and
    the test results.

------------------------------------------------------------------------

Deliverables

-   Screenshots of:
    1.  The rule creation wizard with port 23.
    2.  The inbound rules list showing the block rule.
    3.  The PowerShell test output showing blocked connection.
-   This README.txt documents all steps performed.
