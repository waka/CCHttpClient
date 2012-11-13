# CCHttpClient

HTTP request/response library for Objective-C.
Available HTTP Methods are GET / POST / PUT / DELETE.
To used this, pass to the callback delegate and selector.

## Usage

GET request

    NSString *url = @"http://path/to/get"
    NSDictionary *params = @{@"foo": @"bar"};

    CCHttpClient *client = [CCHttpClient clientWithURL: url];
    [client getWithDelegate: params
                    headers: nil
                   delegate: self
                    success: @selector(handleSuccess:result:)
                    failure: @selector(handleFailure:error:)];

GET JSON request

    NSString *url = @"http://path/to/get"
    NSDictionary *params = @{@"foo": @"bar"};

    CCHttpClient *client = [CCHttpClient clientWithURL: url];
    [client getJSONWithDelegate: params
                        headers: nil
                       delegate: self
                        success: @selector(handleSuccess:result:)
                        failure: @selector(handleFailure:error:)];

POST request

    NSString *url = @"http://path/to/post"
    NSDictionary *params = @{@"foo": @"bar"};

    CCHttpClient *client = [CCHttpClient clientWithURL: url];
    [client postWithDelegate: params
                     headers: nil
                    delegate: self
                     success: @selector(handleSuccess:result:)
                     failure: @selector(handleFailure:error:)];

POST JSON request

    NSString *url = @"http://path/to/post"
    NSDictionary *params = @{@"foo": @"bar"};

    CCHttpClient *client = [CCHttpClient clientWithURL: url];
    [client postJSONWithDelegate: params
                         headers: nil
                        delegate: self
                         success: @selector(handleSuccess:result:)
                         failure: @selector(handleFailure:error:)];

Request success handler

    - (void) handleSuccess: (NSHTTPURLResponse *)response result: (NSData *)result
    {
        id json = [CCHttpClient responseJSON: result];
        [self buildView: json];
    }

Request failure handler

    - (void) handleFailure: (NSHTTPURLResponse *)response result: (NSError *)error
    {
        if (response.statusCode == 404) {
            [SVProgressHUD showErrorWithStatus: @"Not found"];
        } else {
            [SVProgressHUD showErrorWithStatus: @"Error"];
        }
    }


And this is similar to PUT and DELETE methods also.
