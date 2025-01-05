

#Unity  #ProjectStructure #CodingStandard #FolderStructure


Unity3D is a powerful suit of tools ( Project IDE , code IDE , and run-time) for game development. Unity support several languages, but the community consensus is to use only C#.

# 1. Pros of Project Structure

Regardless of which convention you choose to use for Unity or other platforms, having a solid project structure is considered a good idea by the majority of the development community.


Having good coding standards and an established project structure is beneficial to your project .


A Hallmark of Getting Thing Done efficiently is to automate what can be automated. once a team has standards and project structure and adopts them (both admittedly time consuming) the time improvements in the daily workflow are notable. There is less discussion on why or how to name things. It just gets done. 

- <b> Consistency </b> -  The project structure has consistency is presentation regardless of team location, spoken language, or individual programmers.
- <b> Maintenance </b> - Consistent project structure will aid readability. Readability helps new and existing programmers revisit the coed base for fixes and improvements.
- <b> Communication </b> - developers more implicitly understand each other in written and verbal communication.
![[Unity Best Practice/Unity Best Practices.png]]

## Root Folder Structure 

Note here that  "Unity" is a child of the root. This support repos to scale up easily to have Unity and Non Unity content as is often the case in production.

```bash 
	GitHubRepo
	|--- .gitignore
	|--- README.md
	|---Unity
		|--- Assets
		|--- Packages
		|--- ProjectSettings
```

## Assets Folder Structure

let's assume my company "RMC" has a project called "My Project".

Note that the "Art" folder consolidates the files most commonly touched by non programmers. To aid team-workflow, these are centralized. 

Here is the recommended structure.

```bash 
Assets
├── 3rdParty
│   └── [CompanyName]
│       └── [PackageName]
│           ├── Version.txt (With source URL, changelog)
│           └── [PackageName]       
├── Art
│   ├── Animation
│   │   ├── AnimationClips 
│   │   └── Animators
│   ├── Audio
│   │   ├── AudioClips
│   │   └── AudioMixers
│   ├── Fonts
│   ├── Materials
│   ├── Models
│   ├── PhysicMaterials
│   ├── Shaders
│   ├── Sprites
│   └── Textures
│   └── Timeline
│   └── UIToolkit
│       └── Resources
│           ├── Layouts
│           ├── Settings
│           ├── Styles
│           └── Themes
├── Documentation
├── Prefabs
│   └── RMC
│       └── [MyProject]
│           └── MyHeroPrefab (using MyHero.cs)
├── Presets
├── Resources
├── Scenes
├── ScriptableObjects
│   └── RMC
│       └── [MyProject]
│           └── MyHeroSettings (using MyHeroSettings.cs)
├── Scripts
│   ├── Editor
│   │   ├── RMC.MyProject.Editor.asmdef
│   │   └── RMC
│   │       └── [MyProject] (namespace RMC.MyProject)
│   │           └── MyHeroEditor.cs 
│   ├── Runtime
│   │   ├── RMC.MyProject.Runtime.asmdef
│   │   └── RMC
│   │       └── [MyProject] (namespace RMC.MyProject)
│   │           ├── MyHero.cs 
│   │           └── MyHeroSettings.cs
│   └── Tests
│       ├── Editor
│       │   ├── RMC.MyProject.Editor.Tests.asmdef
│       │   └── RMC
│       │       └── [MyProject] (namespace RMC.MyProject)
│       │           └── MyHeroTest.cs 
│       └── Runtime
│           ├── RMC.MyProject.Runtime.Tests.asmdef
│           └── RMC 
│               └── [MyProject] (namespace RMC.MyProject)
│                   └── MyHeroTest.cs 
└── Settings
```


## UI Toolkit Folder Structure

#UIToolkit 

- <b> Resources </b> - All assets are within Resources. Some may be loaded at runtime, so this simple folder structure supports that and is also clean and readable.
- <b> Scripts </b> - I did not put a Scripts folder here. In the future, I might. Any 'Layout' component here can indeed be replaced with a C# component so it may sense to have them sit in this section. For now, I use <i> /Assets/Scripts/ </i> for such cases. 

```bash 
Assets
├── ...       
├── Art
│   ├── ...
│   └── UIToolkit
│       └── Resources
│           ├── Layouts
│           ├── Settings
│           ├── Styles
│           └── Themes
└── ...	
```


# 2. Unity C# Coding Standards

- <b> Integration </b> - The code, the review of the code, and your team are more tightly integrated. Theoretically, the code is more interoperable (Copy / Paste) and mutually intelligible.
- <b> Ownership </b> - More consistency in coding standards across a code-base encourages Collective Ownership, the feeling of respect, care, and reverence developers for their own work and for those who contribute thoughtfully to their own work. 


## Naming Conventions
- <b> Naming/Coding Conventions </b> - name and capitalize the custom keywords 
- <b> Style Conventions </b>
- <b> Lower Camel Case </b>
- <b> Upper Camel Case (aka Pascal Case) </b>

## Coding Templates
```bash 
namespace RMC.Templates
{
     //  Namespace Properties ------------------------------
     //  Class Attributes ----------------------------------
     /// <summary>
     /// Replace with comments...
     /// </summary>
     public class TemplateComponent : MonoBehaviour
     {
          //  Events ---------------------------------------
          //  Properties -----------------------------------
          public string SamplePublicText  
          {  
               get  {  return _samplePublicText;   } 
               set  {  _samplePublicText = value;  } 
          }
          //  Fields ---------------------------------------
          private string _samplePublicText;
          //  Unity Methods   ------------------------------
          protected void Start ()
          {
          
          }
          //  Other Methods --------------------------------
          public string SamplePublicMethod (string message) 
          {
               return message;
          }
          //  Event Handlers -------------------------------
          private void Target_OnCompleted(string message) 
          {
          }
     }
}
```

# 3. Overview of Unity

Unity is a versatile game engine that provides essential features like #UI, #Input , #audio , #rendering , #graphics , #Animation , and #Scripting with C#. Beyond these basics, Unity offers optional service like #multiplayer #gaming, #analytics, #Ads , and #monetization . Unity can be used across all stages of the software development life cycle but is most commonly utilized during the development phase. This phase involves coding, integrating #art #assets, and finally testing and deploying to your chosen platform.

## Key Features of Unity
- <b> UI and Input </b> :  Easy-to-use interfaces and flexible input options.
- <b> Audio and Graphics </b> :  Advanced #Audio management and stunning graphical capabilities.
- <b> Animation and Scripting </b> : Smooth #Animation tools and powerful C# scripting.
- <b> Optional Services </b> : #multiplayer , #analytics ,#ads , and #monetization #tools.
## Unity Best Practices

#### Version Control and Unity Versions

Using version control, such as #git and #Github , is essential for backing up your project, sharing it with others, and maintaining version history. It's advisable to work with the latest #Long-Term-Support (LTS) version of Unity for stability and support. While exploring new features is exiting, for serious projects, sticking to LTS versions is recommended to minimize risks. 

![[Unity Best Practices-1.png]]

### Efficient Settings and Structures

Optimizing your settings can significantly enhance your development workflow. For instance, using #IL2CPP can improve game performance across platforms. Enabling " Enter Play Mode Options" can reduce compile times, though it requires specific code setups for stability.

Unity's "Addressable" system is another powerful tool, replacing the order "Asset Bundles." #Addressable allow you to manage and optimize your game's assets more effectively, improving both delivery and memory usage.

### Design #Principles and #Patterns

Adopting solid design principles like #DRY ( Don't Repeat Yourself) and #KISS (Keep It Simple, Stupid) can streamline your development process.
Standards such as organized project structures and consistent coding practices enhance maintainability and team collaboration. #DesignPatterns provide solutions for common problems, and frameworks and architectures build on these to manage larger complexities.

When starting a project, it's beneficial to consider these practices from the beginning. For instance, dividing your game into manageable scenes and using prefabs can simplify development and maintenance.

## Advanced Practices and #Automation

### Scriptable Objects and Packages

Scriptable Objects offer an alternative to #Monobehaviour  #scripts  for storing #data , enhancing both #editor-time and runtime efficiency. Additionally, incorporation packages like #async / #await  Libraries, #localization, #Unity's #input system, and #UIToolkit from the start can provide significant advantages.

### Automated #Workflows

Automating your build process can save time and reduce errors. Set up automated builds that trigger upon code commits, and include automated unit test to ensure code reliability. This approach ensures that you and your team can quickly identify and address issues. 

For example, making any scene loadable directly from the editor and having a project that automatically build itself can drastically improve development efficiency. Automated unit test further enhance maintainability and scalability. 

### Coding Standards and Project Templates 

Establishing and adhering to coding standards is crucial for team consistency and readability. A well-structured project template can also streamline development. Here's an example of a recommended project folder structure : 

![[Unity Best Practices-3.png]]
- **Third Party**: External libraries.  
- **Art**: Sprites, images, animations, models.  
- **Documentation**: Readme files, links, diagrams.  
-  #Prefabs, #Scenes, #Resources: Unity-specific components.  
- #Scripts: Divided into #Editor, #Runtime, and Test folders.


# 4. Unit Testing 
#UnitTesting

## Understanding the Basic of Unity Testing

Testing in Unity is not just a task ; it's an art. IT involves verifying that every component of game . This process is crucial for ensuring a seamless player experience. For beginners, the concept might seem daunting, but with the right guidance, mastering this art becomes an achievable goal.

#### Key Concepts and Tools
- <b> Unit Testing </b> :  The backbone of testing in Unity, focusing on individual components.
- <b> Integration Testing </b> : Ensures different parts of the game work together harmoniously. 
- <b> Automated Testing </b> : Time-saving tools that automate repetitive testing tasks.

#### Implementing Effective Testing #Strategies

Developing a robust testing strategy is vital. This chapter delves into best practices for setting up executing test, ensuring that every aspect of game is rigorously checked.

#### Best Practices for Unity Testing 
- <b> Regular Testing </b> : Consistently test throughout the development cycle.
-  <b>Test-Driven Development </b> : Start with testing in mind to streamline workflow.
- <b> Automated vs. Manual Testing </b> : Finding the right balance.
#### Exploring Advanced Testing Tools
- <b> Mocking and Stubbing </b> : Simulating components for isolated testing.
- <b> Performance Testing </b> :  Ensuring your game runs smoothly under various conditions
- <b> Continuous Integration ( CI) </b> : Integrating testing into development pipeline. 

# 5. CI/CD With Unity Buildalon


### CI/CD

Game development environment, continuous integration and continuous delivery ( #CI / #CD) have become essential. They streamline the process of #building, #testing, and deploying projects, enabling teams to release software faster and with fewer errors. By integrating frequently and automating builds and tests, game developers can reduce manual work and catch issues early 
![[Unity Best Practices-4.png]]

#### CI/ CD Benefits
- Higher code quality
- Faster deployment
- Reduce production time
- Reduce costs / tech debt

#### CI /CD For Unity

Unity Projects are serious software and these best practices and workflows are available. There are countless options to setup automated builds with the Unity Engine. 

##  #Buildalon For Unity 

Unity Buildalon offers a tailored  CI/CD experience designed specifically for developers. It supports #cross-platform builds #Automation  of #repetitive #task , and smooth integration with popular version control systems like #git.

Whether you're working on #mobile , #desktop ,  or #console games, #Unity #Buildalon allows you to focus on development while it handles the heavy lifting of testing and deployment. 

- <b> Cross-Platform Build Automation </b> :  Easily configure automated builds for #iOS , #Android , #Windows , #macOS , and more.
- <b> Version Control Integration </b> : Seamless #Github integration ensure that project is always in sync with the latest codebase.
- <b> Automated Testing </b> : Unity Buildalon runs your tests across platforms, ensuring that your game works as expected before reaching the player.