# JHUIViewControllerDecoupler
UIViewController Decouple

```
/// string -> controller, with some parameters.return `nil` if not exist.
+ (UIViewController *)jh_controllerFromString:(NSString *)string
                                     paramter:(NSDictionary *)dictionary;
```

### in base UIViewController:
```
/// push a specified VC
- (void)pushSpecifiedVC:(NSString *)VCString parameter:(NSDictionary *)dic{
    UIViewController *vc = [JHUIViewControllerDecoupler jh_controllerFromString:VCString paramter:dic];
    [self.navigationController pushViewController:vc animated:YES];
}

/// present a specified vc
- (void)presentSpecifiedVC:(NSString *)VCString parameter:(NSDictionary *)dic navigation:(BOOL)flag{
    UIViewController *vc = [JHUIViewControllerDecoupler jh_controllerFromString:VCString paramter:dic];
    JHBaseNavigationController *nav = nil;
    if (flag) {
        nav = [[JHBaseNavigationController alloc] initWithRootViewController:vc];
    }
    [self presentViewController:nav?nav:vc animated:YES completion:nil];
}

/// a specified VC
- (UIViewController *)specifiedVC:(NSString *)VCString parameter:(NSDictionary *)dic{
    return [JHUIViewControllerDecoupler jh_controllerFromString:VCString paramter:dic];
}
```
