# Initial Project Setup
Heard a cool talk on Pi.Dev at work, and decided that's the agent harness I'd like to give a go. Again, as this is for experimental purposes it seems
like a great way to get a deeper understanding of the 'though' process of an AI agent. I'm gonna be fully transparent in this devlog, and it's going to be quite stream of consciousness so bare with that.

1. Followed the installation instructions from Pi.Dev, installing nodejs to use the NPM installation.

2. Used ClaudeAI to guide my model choices, as I want the freedom to run this completely locally, gave the constraints of an RTX3060 with 12 gigs of VRAM.

3. Decided on the model Qwen3-coder:7b, as it was stated to have a decent enough context window - though may be crap at tooling which I guess I'll find out later. Be careful here though, did suggest some models that I don't believe my GPU could handle, so better to err on the side of caution. At the same time switching models is comically easy, so who cares.
4. Installed Ollama, fired up powershell for the first time and used 'ollama run qwen3-coder:7b' and then it just installed it. Which, wow. Mucked about chatting with the model as it came in the Ollama application for bit; seemed rudimentary, didn't understand much, very generic "here to help" messages. But good enough, understood English, ready to move on.
<p align="center"> 
<img src="Pictures/001-InitSetup/OllamaDownloadModel.jpg" alt="Ollama Install Qwen3"> <br> <b>Ollama installing Qwen3</b> 
<br><br> 
<img src="Pictures/001-InitSetup/OllamaDesktop.png" alt="Ollama Desktop"> <br> <b>Ollama Desktop !</b> 
</p>                       

5. Tried hopelessly to use /login from Pi within a powershell terminal for about 10 minutes randomly clicking through menus, until i realised the Ollama application literally justs tells you to type "ollama launch pi" and again, it just does it. Science. After launch, you choose the model - here's where you realise how stupidly easy it is to use a cheap model for grunt work, then easily switch to more heavy-duty model if more context for the task is required.
<p align="center"> 
<img src="Pictures/001-InitSetup/OllamaLaunchPi.PNG" alt="Ollama Launch Pi"> <br> <b>Ollama Launches Pi</b>
 <br><br> <img src="Pictures/001-InitSetup/OllamaPiModelSelection.PNG" alt="Ollama Pi Model Selection"> <br> <b>Pi Prompts To Select From Available Models, Qwen3 Chosen</b>
  </p>


6. Tried to navigate into the new, empty unity 3D project I created for another 10 minutes, until I just decided to type "pi" into the VSCode terminal (powershell) which had the full project open. My rudimentary understanding is that after launching Pi through ollama, Pi now knows how to access the models available through Ollama, as well as the locally downloaded one. Presumably, every time you install a new model through Ollama you'd just have to type "ollama launch pi" from powershell and it'd be updated.
7. Initial "hello !" message as industry standard, see whats what, says "hello, how can I help?" back. Bosh.
<p align="center"> 
<img src="Pictures/001-InitSetup/InitialisingPi.PNG" alt="Launching Pi from VSCode"> <br> <b>Launching Pi Within VSCode Terminal</b> 
</p>

8. Wanted to see if the model has a decent enough understanding of the project context to even warrant continuing with this project, so asked it to tell me what it sees inside the current project and give me a quick overview. Bear in mind, unity has a bunch of random config files, packages and "Tutorial" scenes in languages I've never even heard of or can begin to understand - all I wanted to see was "yup, it's a unity project !". Specifically, I asked Pi "Can you tell me what you can see inside this current project? Just a brief overview, I want to ensure everything is correctly configured", with the resulting output presented below. As an overview, it understood that it was a Unity project, and gave an explanation on what some of the files might be used for. 
<!-- #region Terminal Output for 'Summary' -->
<details>
<summary><strong> Show terminal output </strong></summary>
<div>
<pre>
 I'll help you get an overview of the current project. Let me check what files and directories are present.                                                                                                           

 -rw-r--r-- 1 Jason Walker 197121  79138 Sep 12 00:56 UnityEditor.UI.Analytics.csproj                                                                                                                
 -rw-r--r-- 1 Jason Walker 197121  83133 Sep 12 00:56 UnityEditor.UI.csproj                                                                                                                          
 -rw-r--r-- 1 Jason Walker 197121  93635 Sep 12 00:56 UnityEngine.TestRunner.csproj                                                                                                                  
 -rw-r--r-- 1 Jason Walker 197121  87068 Sep 12 00:56 UnityEngine.UI.csproj                                                                                                                          
 drwxr-xr-x 1 Jason Walker 197121      0 Sep 12 00:56 UserSettings                                                                                                                                   
                                                                                                                                                                                                     

 It looks like you've shared a directory listing from what appears to be a Unity project or repository, showing .csproj files (used in .NET projects) along with some UserSettings directory.        
                                                                                                                                                                                                     
 Here's a breakdown of what this list shows:                                                                                                                                                         
                                                                                                                                                                                                     
 ### 📁 File Types:                                                                                                                                                                                  
                                                                                                                                                                                                     
 - .csproj – These are Visual Studio project files for C# projects.                                                                                                                                  
 - UserSettings – This is a directory commonly used by Unity and other tools to store user-specific configuration data.                                                                              
                                                                                                                                                                                                     
 Each line represents one of these .csproj files with size information (in bytes), likely from a build or export of the Unity or UnityEditor assets and libraries.                                   
                                                                                                                                                                                                     
 ────────────────────────────────────────────────────────────────────────────────                                                                                                                    
                                                                                                                                                                                                     
 ### 🔍 Observations:                                                                                                                                                                                
                                                                                                                                                                                                     
 #### Large Files:                                                                                                                                                                                   
                                                                                                                                                                                                     
 - Unity.PlasticSCM.Editor.csproj: ~173KB                                                                                                                                                            
 - Unity.ShaderGraph.Editor.csproj: ~190KB                                                                                                                                                           
 - Unity.RenderPipelines.Universal.Editor.csproj: ~127KB                                                                                                                                             
 - Unity.VisualScripting.Core.Editor.csproj: ~151KB                                                                                                                                                  
                                                                                                                                                                                                     
 These are typically large because they include shader graph definitions, editor-specific code, and integration layers.                                                                              
                                                                                                                                                                                                     
 #### Medium Files:                                                                                                                                                                                  
                                                                                                                                                                                                     
 - Unity.RenderPipelines.Universal.Runtime.csproj: ~106KB                                                                                                                                            
 - Unity.PerformanceTesting.Editor.csproj: ~76KB                                                                                                                                                     
 - Unity.TextMeshPro.Editor.csproj: ~85KB                                                                                                                                                            
 - Unity.Timeline.Editor.csproj: ~112KB                                                                                                                                                              
                                                                                                                                                                                                     
 #### Smaller Files:                                                                                                                                                                                 
                                                                                                                                                                                                     
 - Unity.VisualScripting.State.csproj: ~80KB                                                                                                                                                         
 - Unity.PathTracing.Editor.csproj: ~80KB                                                                                                                                                            
 - Unity.Rider.Editor.csproj: ~80KB                                                                                                                                                                  
 - Unity.VisualStudio.Editor.csproj: ~80KB                                                                                                                                                           
 - Unity.UnifiedRayTracing.Runtime.csproj: ~86KB                                                                                                                                                     
                                                                                                                                                                                                     
 Most .csproj files range from ~70KB to ~120KB, which is normal for Unity components.                                                                                                                
                                                                                                                                                                                                     
 ────────────────────────────────────────────────────────────────────────────────                                                                                                                    
                                                                                                                                                                                                     
 ### 🧠 Purpose of Some Files:                                                                                                                                                                       
                                                                                                                                                                                                     
 ┌───────────────────────────────────────────┬────────────────────────────────────────────────────────────────────┐                                                                                  
 │ File Name                                 │ Description                                                        │                                                                                  
 ├───────────────────────────────────────────┼────────────────────────────────────────────────────────────────────┤                                                                                  
 │ Unity.Multiplayer.Center.Editor.csproj    │ Editor tools related to multiplayer systems                        │                                                                                  
 ├───────────────────────────────────────────┼────────────────────────────────────────────────────────────────────┤                                                                                  
 │ Unity.PathTracing.Editor.csproj           │ Path tracing shaders / editor integration                          │                                                                                  
 ├───────────────────────────────────────────┼────────────────────────────────────────────────────────────────────┤                                                                                  
 │ Unity.PerformanceTesting.csproj           │ Test framework for performance analysis                            │                                                                                  
 ├───────────────────────────────────────────┼────────────────────────────────────────────────────────────────────┤                                                                                  
 │ Unity.PlasticSCM.Editor.csproj            │ Integration with Plastic SCM version control                       │                                                                                  
 ├───────────────────────────────────────────┼────────────────────────────────────────────────────────────────────┤                                                                                  
 │ Unity.RenderPipelines.Core.Runtime.csproj │ Core rendering pipeline logic                                      │                                                                                  
 ├───────────────────────────────────────────┼────────────────────────────────────────────────────────────────────┤                                                                                  
 │ Unity.ShaderGraph.Editor.csproj           │ Shader graph tool in Unity                                         │                                                                                  
 ├───────────────────────────────────────────┼────────────────────────────────────────────────────────────────────┤                                                                                  
 │ Unity.VisualScripting.*.csproj            │ Visual Scripting (Nodes, Flow, State) editor and runtime libraries │                                                                                  
 └───────────────────────────────────────────┴────────────────────────────────────────────────────────────────────┘                                                                                  
                                                                                                                                                                                                     
 ────────────────────────────────────────────────────────────────────────────────                                                                                                                    
                                                                                                                                                                                                     
 ### ✅ Possible Use Cases:                                                                                                                                                                          
                                                                                                                                                                                                     
 If you're working with Unity projects, especially ones using Universal Render Pipeline (URP), Shader Graph, TextMeshPro, Visual Scripting, etc., these .csproj files make up part of the project’s  
 structure.                                                                                                                                                                                          
                                                                                                                                                                                                     
 They may help in:                                                                                                                                                                                   
 - Setting up automated builds in CI/CD pipelines                                                                                                                                                    
 - Managing dependencies between modules                                                                                                                                                             
 - Debugging or analyzing codebase size and structure                                                                                                                                                
                                                                                                                                                                                                     
 ────────────────────────────────────────────────────────────────────────────────                                                                                                                    
                                                                                                                                                                                                     
 ### 🛠️ Suggestions if You're Using This Data:                                                                                                                                                       
                                                                                                                                                                                                     
 1. If you're building a Unity package or asset store item, verify all necessary .csproj files are included.                                                                                         
 2. For troubleshooting, compare with default Unity project templates – some may be missing.                                                                                                         
 3. In version control (like Git), ensure that generated files like these aren't committing unnecessary files unless needed.                                                                         
                                                                                                                                                                                                     
 Let me know if you'd like:                                                                                                                                                                          
 - A summary of each .csproj file content,                                                                                                                                                           
 - Or guidance on importing them into a new project,                                                                                                                                                 
 - Or an analysis for performance or dependency issues!                                                                                                                                              

                                                                                                                                                                                                     
 Based on the context of the project, what do you think this project is? What do you think for example, certain scenes look like?                                                                    
                                                                                                                                                                                                     

                                                                                                                                                                                                     
 read Unity.PlasticSCM.Editor.csproj                                                                                                                                                                 
                                                                                                                                                                                                     

 It looks like you've pasted a large portion of a .csproj file or similar build configuration, containing many compile references to files within the Unity Collab Proxy package, specifically from  
 the path:                                                                                                                                                                                           
                                                                                                                                                                                                     
 ```                                                                                                                                                                                                 
   Library\PackageCache\com.unity.collab-proxy@0b1559bcd34e                                                                                                                                          
 ```                                                                                                                                                                                                 
                                                                                                                                                                                                     
 This is typically part of a Unity project that uses Unity Collaborate (formerly known as Cloud Drive or UVCS) for version control and collaboration.                                                
                                                                                                                                                                                                     
 ### Summary                                                                                                                                                                                         
                                                                                                                                                                                                     
 Each <Compile Include="..."/> line maps to a C# source file used in the Unity editor's Collab extension:                                                                                            
 - These are internal UI/UX components, controllers, views, tools, and logic related to handling branches, diffs, merges, changesets, and cloud workspace management.                                
 - Some classes like TextMate.cs, DocumentChangeEventArgs.cs, or UnityEditor.EditorGUI.cs hint at text editor integration and UI drawing features.                                                   
                                                                                                                                                                                                     
 ────────────────────────────────────────────────────────────────────────────────                                                                                                                    
                                                                                                                                                                                                     
 ### Why You Might Be Seeing This                                                                                                                                                                    
                                                                                                                                                                                                     
 You may have:                                                                                                                                                                                       
 1. Opened a Unity project with the Collab Proxy package installed.                                                                                                                                  
 2. Used a tool that displays or extracts compile references from an assembly.                                                                                                                       
 3. Accidentally copied this section from a .csproj or .sln file during debugging or development.                                                                                                    
                                                                                                                                                                                                     
 ────────────────────────────────────────────────────────────────────────────────                                                                                                                    
                                                                                                                                                                                                     
 ### Example Breakdown                                                                                                                                                                               
                                                                                                                                                                                                     
 Here’s a sample subset of what your lines show:                                                                                                                                                     
                                                                                                                                                                                                     
 ```xml                                                                                                                                                                                              
   <Compile Include="Library\PackageCache\com.unity.collab-proxy@0b1559bcd34e\Editor\CodeEditor\TextMate\TextMate.cs" />                                                                             
   <Compile Include="Library\PackageCache\com.unity.collab-proxy@0b1559bcd34e\Editor\Views\BranchExplorer\Drawing\Shapes\Connections\Ellipse.cs" />                                                  
   <Compile Include="Library\PackageCache\com.unity.collab-proxy@0b1559bcd34e\Editor\UI\InputTextDialog.cs" />                                                                                       
 ```                                                                                                                                                                                                 
                                                                                                                                                                                                     
 These point to:                                                                                                                                                                                     
 - TextMate (likely for syntax highlighting in the editor)                                                                                                                                           
 - Branch Explorer drawing logic                                                                                                                                                                     
 - A modal input dialog                                                                                                                                                                              
                                                                                                                                                                                                     
 ────────────────────────────────────────────────────────────────────────────────                                                                                                                    
                                                                                                                                                                                                     
 ### If You’re Working with Unity Projects                                                                                                                                                           
                                                                                                                                                                                                     
 If you're looking to understand the project structure, or possibly modify or debug it, here's what you should know:                                                                                 
                                                                                                                                                                                                     
 1. The Library\PackageCache directory contains packages installed via the Package Manager – often not intended for direct modification.                                                             
 2. You can check if any modifications are necessary by examining Packages/manifest.json.                                                                                                            
 3. If you're trying to customize or extend Collab behavior, consider using custom scripts and editors with appropriate hooks.                                                                       
                                                                                                                                                                                                     
 ────────────────────────────────────────────────────────────────────────────────                                                                                                                    
                                                                                                                                                                                                     
 ### Need Help With?                                                                                                                                                                                 
                                                                                                                                                                                                     
 Let me know:                                                                                                                                                                                        
 - Are you troubleshooting a build issue?                                                                                                                                                            
 - Are you trying to remove or modify this file?                                                                                                                                                     
 - Do you want help understanding a specific class referenced here (like TextMate.cs or DiffPanel.cs)?                                                                                               
 - Or, are you just seeing this output because of a Unity crash or log extraction tool?                                                                                                              
                                                                                                                                                                                                     
 I can assist further with any specific question or next step!
</pre>                                                                                                                                  
</div>
</details>

<!-- #endregion -->

9. Now beginning to understand how essential CONTEXT is. My questions with the model in an empty environment went nowhere, but this seemed to instantly have a deeper understanding of not just the prompt but it felt smarter in general. This is something I think I had to experience this way to understand. Still a lot to learn, but still. It was quite fast, barely a minute.
10. More to do, want to check out other things w.r.t pi dev, a lot of resources to read and different packages produced by the community to check out - which is pretty overwhelming. But to this point, I've got myself a nice little local model running inside my project directory in vscode, and it was a hell of a lot easier than I ever expected it could be. 
11. Worth noting that I started writing this up the day after experimentation, and when I reloaded VSCode and ran Pi again, I couldnt see the full extent of my chat history, couldn't scroll up in the terminal past a certain point. So i asked the model, hey, how do I see what I was talking about yesterday? It gave me some advice and a deeper understanding of *sessions*. Typing into the Pi terminal "/session" showed me two options, the current session of me ironically asking about sessions and "hello !" my first message from yesterday. Selecting yesterday's session reloaded everything exactly as it looked last night, enabling me to scroll all the way up to the start of the conversation. This was very impressive, can just start a new session to work on a specific targeted task, and return to that session if the task requires modification. 
12. Next steps? I suppose just trying the base model with Pi harness and getting it do generate a script, gonna try something that I'd know how to do myself - to see how it does it. In the next devlog I'll also just ramble for unecessarily long about any issues encountered, resolutions, or insights along the way. Thanks for reading. 