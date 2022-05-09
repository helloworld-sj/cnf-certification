# How to submit CNF Certification results

## The tests
The standard set of CNF Certification tests is currently those defined by the [cnf-certification] (TBD) tag in the [CNF Test Suite](https://github.com/cncf/cnf-testsuite/blob/main/docs/LIST_OF_TESTS.md).

## Prereqs

**K8s Cluster**
- [Access](https://kubernetes.io/docs/tasks/access-application-cluster/access-cluster/) to a working [Certified K8s](https://cncf.io/ck) cluster using the [containerd](https://containerd.io/) runtime

**Workstation**
- Linux OS
- wget and curl binaries available in PATH
- Public internet access for downloading dependencies
- An admin `kubeconfig` file referenced from the [KUBECONFIG environment variable](https://kubernetes.io/docs/tasks/access-application-cluster/configure-access-multiple-clusters/#set-the-kubeconfig-environment-variable). (See [K8s Getting started guide](https://kubernetes.io/docs/setup/) for options)

If you do not have a K8s cluster running, you can deploy your own cluster with [various tools](https://kubernetes.io/docs/setup/) or use a [public cloud or turnkey solution](https://kubernetes.io/docs/setup/production-environment/turnkey-solutions/)

Kind is one option tested and supported by the CNF Test Suite team.  Follow the [kind install](KIND-INSTALL.md) instructions to setup a cluster in [kind](https://kind.sigs.k8s.io/)


## Running
The standard tool for running these tests is the [CNF Test Suite](https://github.com/cncf/cnf-testsuite). 

1. Download the [certification binary release](http://URL_to_specific_release) of the test suite
1. Run setup to prepare the cnf-testsuite: `cnf-testsuite setup`
3. Create a configuration file for testing your CNF
    1. Review the [CNF_TESTSUITE_YML_USAGE.md](CNF_TESTSUITE_YML_USAGE.md) document on formatting and other requirements.
    1. Create a cnf-testsuite.yml with the required information
4. Initialize the test suite for using the CNF: `cnf-testsuite cnf_setup cnf-config=./cnf-testsuite.yml`
5. Run the certication tests: `cnf-testsuite cert`

The results file will be saved to: results/cnf-testsuite-results-YEAR-MMDD-HHMMSS-NNN.yml

Example:
- Test results have been saved to results/cnf-testsuite-results-2022-0412-201220-225.yml

NOTE: The results file and the config file are required in the submission results.


<!--1. Pull down an example CNF configuration to try: curl -o cnf-testsuite.yml https://raw.githubusercontent.com/cncf/cnf-testsuite/main/example-cnfs/coredns/cnf-testsuite.yml-->




## Uploading