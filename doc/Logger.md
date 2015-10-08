## Logger Overview ##
Logger: a simple class to log symbols (either number or string) during training, and automate plot generation.

## Logger Example ##
``` lua
    logger = optim.Logger('somefile.log')    -- file to save stuff
    logger:setNames{'training error', 'test error'}
    for i = 1,N do                           -- log some symbols during
       train_error = ...                     -- training/testing
       test_error = ...
       logger:add{train_error, test_error}
    end
```
or 
``` lua
    logger = optim.Logger('somefile.log')    -- file to save stuff
    for i = 1,N do                           -- log some symbols during
        train_error = ...                     -- training/testing
        test_error = ...
        logger:add{['training error'] = train_error,
            ['test error'] = test_error}
    end
    logger:style{['training error'] = '-',   -- define styles for plots
                 ['test error'] = '-'}
    logger:plot()                            -- and plot
```

