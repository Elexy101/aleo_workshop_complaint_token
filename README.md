# aleo_workshop_complaint_token
The smart contract is a compliant token contract built on the Aleo blockchain. It is designed to ensure that token transfers adhere to regulatory and security standards, such as KYC (Know Your Customer) verification, spending limits, and jurisdictional restrictions.

# Key Features and Functionalities
1. Token Registration & Minting

- The token is registered with the Aleo Token Registry to ensure compliance.
- The contract mints a fixed supply of tokens, which can only be done once by an admin account.

2. KYC & Compliance Mechanisms

- KYC Approval: The admin can approve users by adding them to the KYC whitelist.
- Blacklisting: The admin can revoke a user's KYC approval, preventing them from transacting.
- Jurisdiction Restrictions: The admin can restrict or lift bans on transactions in specific countries.

3. Controlled Token Transfers

- Tokens can only be transferred privately if:
- Both the sender and recipient are KYC-approved.
- The recipient’s country is not restricted.
- Users have a daily spending limit, ensuring that they do not exceed a maximum transaction threshold in a single day.

4. Spend Limit Enforcement

- Each user has a spend limit record that tracks their spending per day (epoch-based).
- If a user tries to exceed the allowed daily spend, the transaction will be rejected.

5. Security and Authorization

- The contract pre-authorizes token transfers before they are executed.
- The admin has control over minting, KYC approvals, and jurisdiction restrictions.
- Transactions are finalized using asynchronous processing (Future) to improve performance.

# OUTPUT PREVIEW
initialize token: 
`leo run initialize` This function sets up the token when the contract is first deployed. It usually defines the token name, symbol, supply, and admin privileges
```

⛓  Constraints

 •  'token_registry.aleo/register_token' - 3 constraints (called 1 time)
 •  'elexy_complaint_token.aleo/initialize' - 6,715 constraints (called 1 time)

➡️  Output

 • {
  program_id: elexy_complaint_token.aleo,
  function_name: initialize,
  arguments: [
    {
      program_id: token_registry.aleo,
      function_name: register_token,
      arguments: [
        {
  token_id: 71619063553950105623552field,
  name: 71619063553950105623552u128,
  symbol: 71619063553950105623552u128,
  decimals: 6u8,
  supply: 0u128,
  max_supply: 10000000000000000u128,
  admin: aleo1ptelhnd8l2fy8a2kf0hwns9n8mcvxwz7al479uxhpk5cwsfrhqzs8mnhxx,
  external_authorization_required: true,
  external_authorization_party: aleo1ptelhnd8l2fy8a2kf0hwns9n8mcvxwz7al479uxhpk5cwsfrhqzs8mnhxx
}
      ]
    }
  
  ]
}
```

mint_private :
`leo run mint_private` This function creates new tokens privately and assigns them to a specific user. only the admin can call this function, and it follows compliance rules.

```
⛓  Constraints

 •  'token_registry.aleo/mint_private' - 5,366 constraints (called 1 time)
 •  'elexy_complaint_token.aleo/mint_private' - 10,833 constraints (called 1 time)

➡️  Outputs

 • {
  owner: aleo1f5enhpxfz3l3pqyh8k9d5xkqu0njv27xp5sv4nedarrk3nrgnuzqm3pp9h.private,
  amount: 1000000000000000u128.private,
  token_id: 71619063553950105623552field.private,
  external_authorization_required: true.private,
  authorized_until: 4294967295u32.private,
  _nonce: 6466053333634125233093396682666498566172994154126431633232060894488044562348group.public
}
 • {
  program_id: elexy_complaint_token.aleo,
  function_name: mint_private,
  arguments: [
    {
      program_id: token_registry.aleo,
      function_name: mint_private,
      arguments: [
        71619063553950105623552field,
        1000000000000000u128,
        true,
        4294967295u32,
        aleo1ptelhnd8l2fy8a2kf0hwns9n8mcvxwz7al479uxhpk5cwsfrhqzs8mnhxx,
        5361752669412399406377505907606720976629368150853882284734737352411964146534field
      ]
    }
  
  ]
}
```

transfer_private: 
This function allows users to send tokens privately from one person to another. The recipient must be KYC-approved and meet compliance conditions

```
⛓  Constraints

 •  'token_registry.aleo/prehook_private' - 4,171 constraints (called 1 time)
 •  'token_registry.aleo/transfer_private' - 4,171 constraints (called 1 time)
 •  'elexy_complaint_token.aleo/transfer_private' - 41,615 constraints (called 1 time)

➡️  Outputs

 • {
  owner: aleo1f5enhpxfz3l3pqyh8k9d5xkqu0njv27xp5sv4nedarrk3nrgnuzqm3pp9h.private,
  amount_spent: 10000u128.private,
  epoch_spent: 89u32.private,
  _nonce: 4144843631994804270902362208569414415868356387466336593427170157615775522937group.public
}
 • {
  owner: aleo1f5enhpxfz3l3pqyh8k9d5xkqu0njv27xp5sv4nedarrk3nrgnuzqm3pp9h.private,
  amount: 999999999990000u128.private,
  token_id: 71619063553950105623552field.private,
  external_authorization_required: true.private,
  authorized_until: 4294967295u32.private,
  _nonce: 8180355700843361702797531685299637714663253714773926798710933149539241771783group.public
}
 • {
  owner: aleo1f5enhpxfz3l3pqyh8k9d5xkqu0njv27xp5sv4nedarrk3nrgnuzqm3pp9h.private,
  amount: 0u128.private,
  token_id: 71619063553950105623552field.private,
  external_authorization_required: true.private,
  authorized_until: 4294967295u32.private,
  _nonce: 7496583812072427892714007472576458059285456769303454333833934808149766782261group.public
}
 • {
  owner: aleo1f5enhpxfz3l3pqyh8k9d5xkqu0njv27xp5sv4nedarrk3nrgnuzqm3pp9h.private,
  amount: 10000u128.private,
  token_id: 71619063553950105623552field.private,
  external_authorization_required: true.private,
  authorized_until: 0u32.private,
  _nonce: 3072917141324152669530532798129752876291093092248943705162696114595500121035group.public
}
 • {
  program_id: elexy_complaint_token.aleo,
  function_name: transfer_private,
  arguments: [
    {
      program_id: token_registry.aleo,
      function_name: prehook_private,
      arguments: [
        71619063553950105623552field,
        aleo1ptelhnd8l2fy8a2kf0hwns9n8mcvxwz7al479uxhpk5cwsfrhqzs8mnhxx
      ]
    },
    {
      program_id: token_registry.aleo,
      function_name: transfer_private,
      arguments: [
        true,
        4294967295u32
      ]
    },
    89u32,
    aleo1f5enhpxfz3l3pqyh8k9d5xkqu0njv27xp5sv4nedarrk3nrgnuzqm3pp9h,
    aleo1f5enhpxfz3l3pqyh8k9d5xkqu0njv27xp5sv4nedarrk3nrgnuzqm3pp9h,
    234399field
  ]
}
```

set Timelock:
This function locks a user’s tokens for a certain period, preventing them from being transferred. It can be used to enforce holding periods or prevent early withdrawals.

```
⛓  Constraints

 •  'elexy_complaint_token.aleo/set_timelock' - 6 constraints (called 1 time)

➡️  Output

 • {
  program_id: elexy_complaint_token.aleo,
  function_name: set_timelock,
  arguments: [
    aleo1f5enhpxfz3l3pqyh8k9d5xkqu0njv27xp5sv4nedarrk3nrgnuzqm3pp9h,
    0u32
  ]
}
```



# Use Case Scenarios
- Regulated Financial Applications: Ensuring that only verified users can trade or transfer tokens.
- Cross-Border Transactions: Blocking transactions to restricted jurisdictions.
- Corporate Token Management: Allowing companies to enforce spending limits for employees or clients.
- Secure Private Transfers: Ensuring token privacy while complying with regulatory requirements.
