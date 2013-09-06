### Who We Are

* Nick Meyer (@nickmeyer) Co-founder of MileWise, acquired by Yahoo.
* Pierre Maloka (@pmaloka) Worked on HBO GO, NFL Blitz like a baller.
* Pulah Shah (@pulahshah) Winner API Prize PennApps Spring '13.

### PennApps YQL Sample Code

Simple example of using YQL to query craiglist for mustang convertibles. Because who doesn't want a mustang convertible?


![Totally a Mustang.](mustang.jpg)


### Quick Code:

```objective-c
- (void)viewDidLoad
{
  NSString *yqlQuery = @"http://query.yahooapis.com/v1/public/yql?q=select%20*%20from%20craigslist.search%20where%20location%3D%22newyork%22%20and%20type%3D%22sss%22%20and%20query%3D%22mustang%20convertable%22&format=json&diagnostics=true&env=store%3A%2F%2Fdatatables.org%2Falltableswithkeys&callback=";
  NSDictionary *results = [self downloadJSON:yqlQuery];
}

- (NSDictionary *)downloadJSON:(NSString *)query
{
    NSError *error;
    
    NSURLRequest *request = [NSURLRequest requestWithURL:[NSURL URLWithString:query]];
    NSData *response = [NSURLConnection sendSynchronousRequest:request returningResponse:nil error:&error];
    
    if (!response || error) {
        NSLog(@"%@", error.description);
        return nil;
    }
    
    NSDictionary *jsonDictionary = [NSJSONSerialization JSONObjectWithData:response options:kNilOptions error:&error];
    
    if (error) {
        NSLog(@"%@", error.description);
        return nil;
    }
    
    return jsonDictionary;
}

```
