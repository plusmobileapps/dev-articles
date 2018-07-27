# Gradle 3.0 

Ever since the introduction of the Android Gradle 3.0 plugin, there are a couple of changes in the way you configure dependencies. 

Before there use to be only the `compile` dependency configuration, gradle 3.0 ditched `compile` and is now `implementation` and `api`. Now these new dependency configurations do not need to be used if all of the configurations still remain as `compile`. If one `compile` statement is switched to either of the new configurations, then all `compile` configurations in the gradle script need to also be changed to the new configurations.  

### Implementation
`implementation` is what you should try to use all the time as this is where faster build times can come into play if you begin to modularize your app. This is possible because this lets gradle know to not leak this dependency out to other modules, so then only what dependencies are in the current working module will need to be recompiled. 

### API
`api` works the same as `compile` and will leak the dependency to other modules. This is best used when you are creating a library in something like a [base feature module](https://developer.android.com/topic/instant-apps/getting-started/structure.html).  

[Android docs on the new dependency configurations](https://developer.android.com/studio/build/gradle-plugin-3-0-0-migration.html#new_configurations)
