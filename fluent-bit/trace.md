    [OUTPUT]
        Name  es
        Match *
        Host  10.10.10.10
        Port  9200
        HTTP_User 
        HTTP_Passwd 
        tls  On
        tls.verify On
        Suppress_Type_Name On        
        Index index-%Y.%m.%d
        Trace_Error       On
        Trace_Output      On