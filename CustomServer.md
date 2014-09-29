# Custom Harpy

- How To use it.

MiniVersion is the mini Version User need To Install  
UpdateUrl is the CustomServer for Update.
IF You have a Custom Version replace CurrentVersion.

    double MiniVersion = [object[@"MiniVersion"] doubleValue];
    NSURL *updateUrl = [NSURL URLWithString:object[@"UpdateURL"]];
    
    // Check Version.
    /// AppID is Set With iTunes Connect Apple ID.
    [[Harpy sharedInstance] setAppID:@"320203391"];
    [[Harpy sharedInstance] setAppName:@"SETNEWS"];
    [[Harpy sharedInstance] setCountryCode:@"TW"];
    [[Harpy sharedInstance] setUseCustomServer:YES];
    [[Harpy sharedInstance] setCurrentServerVersion:CurrentVersion];
    [[Harpy sharedInstance] setCustomURLUpdate:updateUrl];
    
    /// Use Custom Server
    if ([[[[NSBundle mainBundle] infoDictionary] objectForKey:@"CFBundleVersion"] doubleValue] < MiniVersion) {
        [[Harpy sharedInstance] setCustomResult:YES];
        [[Harpy sharedInstance] setAlertType:HarpyAlertTypeForce];

    }else if ([[[[NSBundle mainBundle] infoDictionary] objectForKey:@"CFBundleVersion"] doubleValue] < [CurrentVersion doubleValue]){ 
        [[Harpy sharedInstance] setCustomResult:YES];
        [[Harpy sharedInstance] setAlertType:HarpyAlertTypeOption];
    }else{
        [[Harpy sharedInstance] setCustomResult:NO];
    }
    
	/// Use App Store.
	if ([[[[NSBundle mainBundle] infoDictionary] objectForKey:@"CFBundleVersion"] doubleValue] <MiniVersion) {
        
        [[Harpy sharedInstance] setAlertType:HarpyAlertTypeForce];
        [[Harpy sharedInstance] checkVersion];
        
    }else if ([[[[NSBundle mainBundle] infoDictionary] objectForKey:@"CFBundleVersion"] doubleValue] >MiniVersion){
        
        [[Harpy sharedInstance] setAlertType:HarpyAlertTypeOption];
        [[Harpy sharedInstance] checkVersion];
    }else{
        [[Harpy sharedInstance] setCustomResult:NO];
    }

