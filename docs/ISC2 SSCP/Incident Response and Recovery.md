**Understand 4.1**
**Support incident lifecycle**
**Preparation**
	incident response policy
	incident response plan
	incident response team
		appropriate training (internal)
		contract (external)
		practice
**Detection, analysis and escalation**
	knowledge of a potential incident can come from a variety of sources
		automated solutions (IDS/IPS, DLP firewall)
		analyst review
		external sources (news, vendors, etc)
		users
	the initial review of a potential incident to determine:
		event/incident/false positive
		intent
		source
		extent
		type
**Containment**
	the initial handling of an incident
		containment/reduce spread
		prevent additional loss
		gather more details
		business needs will determine the actions
**Eradication**
	ensuring total removal of whatever caused the incident
		ie removing malware
		removing any possible tools installed by an attacker
		removing affected devices/software
**Recovery**
	actions performed to return to last known good state
	often entails use of backups
	typically takes much longer than eradication
**Lessons learned/implementation of new countermeasure**
	address the root cause of the incident
		goal: reduce the possibility of reoccurrence
	review the incident response
		determine if future incidents could be avoided
		determine if the response could be improved

**Understand 4.2**
**Forensic investigations**
**Legal and ethical principles**
	Various court systems exist for various purposes, and the security practitioner may be involved in gathering evidence at different levels of scrutiny
		operational (internal): the organization can review any material it wants, for labor decisions
		civil: when the organization has conflicts with other private parties, resulting in litigation; adjudication is based on the "preponderance of evidence" rule
		criminal: when the organization is being prosecuted for a crime; adjudication is based on the "reasonable doubt" standard
		administrative (external): in some jurisdictions (such as the US), regulatory agencies can create their own administrative laws, have their own prosecutors, and their own courts/judges
**Evidence handling**
	preferable to conduct analysis on copies/images of systems/data than the originals
	when handling originals, efforts should be made to avoid alteration (for instance, write-blockers)
		integrity checks enhance believability; hashing is extremely useful
	chain of custody is essential
	use of experts is advisable
		if contracting with a third party for forensic services, a retainer/pre-emptory contract is useful to ensure prompt attention
**Reporting of analysis**
	evidence/analysis may have to be reported to various audiences, including
		judge/jury
		counsel
		arbitrator
		investors
		regulators
		*might have to clear and simple in terms of IT things to convey to this audience*'
	evidence/analysis should have these qualities:
		authentic: does it show what it claims to show?
		complete: is it all the pertinent evidence?
		reliable: would the same collection method, used again, give the same results?
		believable: is the source trustworthy?
		admissible: will the court allow it?

**Understand 4.3**
**Business continuity plan (BCP) and disaster recovery plan (DRP) activities**
**Emergency response plans and procedures**
	regardless of the type of emergency, a plan and process is necessary to maintain critical business functions
		different organizations will have different critical functions/assets, and therefore different plans/procedures
		must have support of senior management
		ties directly to the BIA
		helpful to include all affected business units during development
	HEALTH AND HUMAN SAFETY IS PARAMOUNT
**Interim or alternate processing strategies**
	alternate processing options:
		hot site - most expensive, replicates the critical functions and assets of a normal operating business, ready to go at any notice
		warm site - replicates systems but generally doesn't have a full copy of current data
		cold site - empty facility, but could house personnel performing functions. Longest to resume critical business functions
		cloud/remote work - send people home/hotel and use cloud to perform business functions
		MOU/JOA - Memorandum of understanding / Joint operating agreement
**Restoration planning**
	backup backup backup
		practice restoration from backup
	resuming normal operations too soon can put people and assets at risk
	resuming normal operations too late can cause additional damage
	resume less-sensitive processes first
	may restore to the alternate operating site (new normal)
**Backup and redundancy implementation**
	backups
		full/differential/incremental
		full - all current data from production environment
		differential -  only capture data that's changed since the last full backup
		incremental - only capture data that has changed since last full or incremental backup
	redundancy and resiliency are crucial, especially for the critical path
		the systems, data, infrastructure, and people that are essential to the organization's core business
	redundancy can mean multiple systems actively functioning (which can also aid in load balancing), or an active set with another on standby, or replacement units for active system
**Testing and drills**
	specific personnel need training; those who will take part in the actual response activities
	everyone needs awareness (fire drills, etc)
	common test types you should know:
		Read-through/tabletop
		Parallel
		Full interruption
