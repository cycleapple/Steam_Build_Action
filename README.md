
# Unity Build For Self-Hosted Runner

## Description
This GitHub Action allows you to automate the process of building a Unity project for the Windows 64-bit platform using a self-hosted runner. It facilitates the build process, ensuring that the necessary steps are executed smoothly.

## Inputs
- `unityPath` (required): The full path to the Unity executable.
- `buildPath` (required): The path where the build artifacts will be stored.
- `executeMethod` (required): The name of the Unity method to execute during the build.
- `extraArgument` (required): Extra arguments to pass to the Unity build command.
- `projectPath` (optional): The path to the Unity project. Default is the root of the repository.
- `exeFileName` (required): The name of the .exe file to check for in the build folder.

## Runs On
This action runs using a composite run strategy, ensuring efficient execution of the defined steps.

## Steps
1. **Check if Build Folder Exists**: Verifies if the build folder already exists.
2. **Remove Existing Build Folder**: Removes the existing build folder if it exists.
3. **Create Build Folder**: Creates a new build folder.
4. **Unity Build**: Executes the Unity build process based on the provided inputs.
5. **Check for Custom .exe File**: Verifies if the custom .exe file exists in the build folder.

## Usage
To use this action, follow the steps below:

1. Configure your GitHub workflow to include this action.
2. Provide the necessary inputs such as `unityPath`, `buildPath`, `executeMethod`, `extraArgument`, and `exeFileName`.
3. Run your workflow, and the action will handle the Unity build process for you.

### Example Workflow
```yaml
name: Unity Build Workflow

on:
  push:
    branches:
      - main

jobs:
  build:
    runs-on: self-hosted
    steps:
    - name: Checkout Repository
      uses: actions/checkout@v2
      
    - name: Unity Build
      uses: cycleapple/unity-build-action@v1
      with:
        unityPath: '/path/to/unity/executable'
        buildPath: './Build'
        executeMethod: 'BuildPipeline.BuildPlayer'
        extraArgument: '-developmentBuild'
        projectPath: './UnityProject'
        exeFileName: 'MyGame'
```

## License
This action is licensed under the [MIT License](LICENSE). Feel free to modify and use it according to your needs.
