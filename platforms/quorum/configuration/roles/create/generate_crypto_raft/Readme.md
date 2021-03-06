## ROLE: geerate_crypto_raft
This role generates the crypto material for RAFT consensus

### Tasks

#### 1. Check if nodekey already present in the vault
This tasks checks if nodekey is already present in the vault

**shell**: This module runs the vault read command in a shell

##### Input Variables

    VAULT_ADDR: vault address
    VAULT_TOKEN: vault token

##### Output Variables

    vault_nodekey_result: This variable stores whether the nodekey is present in vault or not.

#### 2. Create build directory if it does not exist
This task creates the build directory if it does not exist

**file**: This module creates the build directory if it does not exist


#### 3. Generate crypto for raft consensus
This task generates crypto material for RAFT consensus

**shell**: This module starts a shell which runs commands to generate crypto


**when**: It runs when *vault_nodekey_result.failed* == True, i.e. when nodekey is not found in vault

#### 4. Copy the crypto material to Vault
This task copies the above generated crypto material to the vault

**shell**: This module is used to put the generated crypto material in the vault

**when**: It runs when *vault_nodekey_result.failed* == True, i.e. when nodekey is not found in vault.

