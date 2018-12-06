# StaticScriptableObject for Unity/Odin Serializer

Class derived from SerializedScriptableObject(Odin) that when inherited, provides a static singleton ScriptableObject. 

When inheriting from this class, the Instance field allows you to access any static methods within the ScriptableObject.

At present, this is intended for a specific use and will automatically load the asset of the ScriptableObject when data is
requested from it, or if it doesn't exist, automatically create and load it. 

When in play-mode, the asset is copied to a new instance such that changes aren't saved back to the ScriptableObject. 

The base class itself derives from Odin Inspector/Serializer's SerializedScriptableObject, but will work as intended with
the Unity ScriptableObject class. 

The preferred use case is to inherit from StaticScriptableObject in a new class and write get and set methods to set the Instance values, rather than making the containers static themselves. Containers can remain private. Odin's serializer allows you to use Dictionaries, Hashsets, etc. 

The asset that is created for the ScriptableObject will be loaded as soon as data is requested if it is not already loaded, and then marked to not be unloaded on scene change. This should ensure the ScriptableObject instance remains in memory for the duration of the game and only loaded once.

The file itself will be created in a hardcoded data structure. This may be possible to change later on but for now, I'll leave it as is.


