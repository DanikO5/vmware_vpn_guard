# vmware_vpn_guard
VPN kill switch for VMware processes. The script continuously monitors for a specific VPN network interface. If the connection drops, it automatically finds and terminates vmware.exe and vmware-vmx.exe to prevent the virtual machine from communicating over an unsecured connection.
