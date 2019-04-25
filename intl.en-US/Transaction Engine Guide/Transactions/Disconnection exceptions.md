# Disconnection exceptions {#concept_yk4_dqk_x2b .concept}

If the current session is in the transaction status, and a partition related to this transaction closes the connection to the session due to an exception, this session closes the connection to the client, and rolls back the transaction.

