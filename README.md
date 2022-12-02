# ML.NET CLI Codespaces

Sample repo that shows how to configure the ML.NET CLI with GitHub Codespaces.

This uses the [.devcontainer.json](./.devcontainer.json) file to create an environment with .NET 6 SDK and ML.NET CLI.

Once the Codespace starts, it downloads the taxi-fare dataset and saves it to the `data` directory.

## Usage

1. Fork repo.
1. Create a new GitHub codespace.
1. Once your codespace starts, use the ML.NET CLI to train a regression model using the taxi-fare dataset. 
    1. Open the integrated terminal
    1. Enter the following command:

        ```bash
        mlnet regression --dataset data/taxi-fare-train.csv --label-col "fare_amount" --name TaxiFareRegression --train-time 60
        ``` 

        The ML.NET CLI begins training. Once training completes, you should see output similar to the following:

            ```text
            ===============================================Experiment Results=================================================            ------------------------------------------------------------------------------------------------------------------            |                                                     Summary                                                    |
            ------------------------------------------------------------------------------------------------------------------
            |ML Task: Regression                                                                                             |
            |Dataset: /workspaces/MLNETCLICodespaces/data/taxi-fare-train.csv                                                |
            |Label : fare_amount                                                                                             |
            |Total experiment time : 29.217 Secs                                                                             |
            |Total number of models explored: 24                                                                             |
            ------------------------------------------------------------------------------------------------------------------

            |                                              Top 5 models explored                                             |
            ------------------------------------------------------------------------------------------------------------------
            |     Trainer                             RSquared Absolute-loss Squared-loss RMS-loss  Duration #Iteration      |
            |17   FastTreeTweedieRegression             0.9511          0.47         4.32     2.08       0.3         17      |
            |20   FastTreeRegression                    0.9378          0.57         5.50     2.35       0.3         20      |
            |11   FastTreeRegression                    0.9272          0.90         6.43     2.54       0.1         11      |
            |13   FastForestRegression                  0.9242          0.94         6.70     2.59       0.5         13      |
            |3    FastForestRegression                  0.9204          0.79         7.03     2.65       0.3          3      |
            ------------------------------------------------------------------------------------------------------------------

            save TaxiFareRegression.mbconfig to /workspaces/MLNETCLICodespaces/TaxiFareRegression
            Generating a console project for the best pipeline at location : /workspaces/MLNETCLICodespaces/TaxiFareRegression            
            ```

    1. When it completes, a new C# console project called `TaxiFareRegression` is created and it contains your model and generated code to retrain and make predictions. 
