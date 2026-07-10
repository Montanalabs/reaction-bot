#! VULNERABLE reaction-bot — feeds the untrusted input straight to the tool, no extraction.
#! check -> UNSAFE: tainted data cannot reach a capability.
grant react

let raw = fetch<web>
privileged { react(raw) }  # tainted -> tool: REJECTED
