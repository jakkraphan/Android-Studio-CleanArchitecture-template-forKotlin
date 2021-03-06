# Android-Studio-CleanArchitecture-template-forKotlin
This is an Android-Studio Template for CleanArchitecture Template & **Kotlin**

This repository is made with reference to  [Android-Studio-MVP-template](https://github.com/benoitletondor/Android-Studio-MVP-template). So, the repository configuration is similar.

It is inspired [Android-CleanArchitecture](https://github.com/android10/Android-CleanArchitecture) and [android-architecture-component](https://github.com/googlesamples/android-architecture-components)

## Support androidX ONLY
V2.X is supported **androidX ONLY!!**.

So, **if your project don't migrate to androidX,please do it first!!**

Or,please use V1.X templates

## Hierarchy
Here's the hierarchy it follows:
```
<Root>
    +--- buildSrc
    |     +--- main
    |           +--- kotlin
    |                  - Dependencies.kt
    |                  - common-library.gradle.kts
    |                  - android-application.gradle.kts
    |  
    |- android-application.gradle.kts
    |- build.gradle.kts
    |
    +--- proguard
          - XXX.pro
          - YYY.pro
          - ...


com.company.app
    +--- data
    |     +--- datasource
    |     |
    |     +--- utils
    |     |     +--- extensions
    |     |            - Observable
    |     |
    |     | - ApiModules
    |     | - RepositoryModules
    |
    +--- domain
    |     +--- entity
    |     |
    |     +--- repository
    |     |
    |     +--- usecase
    |     |
    |     +--- utils
    |     |     +--- commons
    |     |            - ExecutionThreads
    |     |            - UseCase
    |     |
    |     | - UseCaseModules
    |
    +--- presenter
    |     +--- utils
    |     |     +--- annotations
    |     |     |      - ActivityScope
    |     |     |      - ViewModelKey
    |     |     +--- commons
    |     |     |      - BasePresenter
    |     |     |      - BaseView
    |     |     |      - ViewModelFactory
    |     |     |
    |     |     +--- di
    |     |     |      - Injectable
    |     |     |
    |     |     +--- extensions
    |     |            - Activity
    |     |            - Fragment
    |     |            - LiveDataReactiveStreams
    |     |
    |     | - BindingModules
    |
    | - ApplicationModule
    | - MainApplication
    | - RootComponent

res
 +--- layout
 |    - base_activity.xml
```

## Prerequisites
You must satisfy the following conditions.

- [Kotlin](https://kotlinlang.org/)**(Recommended to use [Android-Studio 3.3](https://developer.android.com/studio/preview/index.html))**
- [Dagger2](https://google.github.io/dagger/) for dependency injection
- [RxJava2](https://github.com/ReactiveX/RxJava) for Asynchronous processing.
- [Kotlin Android Extensions](https://kotlinlang.org/docs/tutorials/android-plugin.html) (Default Support)

# Support Main Libraries, Service, Layout,
- [Dagger2](https://google.github.io/dagger/)
- [RxJava2](https://github.com/ReactiveX/RxJava)
- [Realm](https://realm.io/)
- [ConstraintLayout](https://developer.android.com/reference/android/support/constraint/ConstraintLayout.html)
- [Retrofit2](http://square.github.io/retrofit/)
- [Swagger](https://swagger.io/)
- [android-ktx](https://github.com/android/android-ktx)
- [DataBinding](https://developer.android.com/topic/libraries/data-binding/index.html)
- [ViewModel](https://developer.android.com/topic/libraries/architecture/viewmodel.html)
- [Spek2.X](http://spekframework.org/docs/latest/)
- [Mockito](http://site.mockito.org/)
- [robolectric](http://robolectric.org/)
- [Assert-J](http://joel-costigliola.github.io/assertj/)

## Installation

#### For Mac:

- If you have a standard Android Studio installation:

Just run the install script at the root of this repository:

```
./install.sh
```

- Manual installation:

Just copy all 5 directories
- `BaseCleanArchitectureTemplateKotlin`
- `DataTemplateKotlin`
- `DomainTemplateKotlin`
- `PresenterActivityTemplateKotlin`
- `PresenterFragmentTemplateKotlin`
- `PresenterServiceTemplateKotlin`
- `PresenterBroadcastReceiverTemplateKotlin`

and paste to `$ANDROID_STUDIO_FOLDER$/Contents/plugins/android/lib/templates/activities/`

#### For Windows:

Just copy all 5 directories
- `BaseCleanArchitectureTemplateKotlin`
- `DataTemplateKotlin`
- `DomainTemplateKotlin`
- `PresenterActivityTemplateKotlin`
- `PresenterFragmentTemplateKotlin`
- `PresenterServiceTemplateKotlin`
- `PresenterBroadcastReceiverTemplateKotlin`

and paste to  `$ANDROID_STUDIO_FOLDER$\plugins\android\lib\templates\activities\`

## How to Use
#### 1. Generate Base template
First of all, create the base hierarchy and classes using `CleanArchitectureTemplate` from the **root package folder**. This needs to be done only once per project:
![CleanArchitectureTemplate](static/selectBaseTemplate.png "BaseCleanArchitectureTemplateKotlin")

~~Or if you create a new project, please select `CleanArchitectureTemplate` on this screen~~.

**Android Studio 3.3 maybe unsupport to add original Template to Create a new Project Selection**..

Next, you set project config.
- **Application Class Name** -> Set Root ApplicationClass Name
- **Create kotlin src dir?** -> Please check if you have not previously created the kotlin folder
- **Need Realm?** -> Please check this when using [Realm](https://realm.io/)
- **Need Retrofit2?** -> Please check this when using  [Retrofit2](http://square.github.io/retrofit/)
- **Use Swagger?** -> Please check this if the Retrofit API was created by [Swagger](http://swagger.io/)(RxJava2 used)

![Project Config](static/configPrj.png "Project Config")

When all settings are completed click the Finish button!!

#### 2.FIX build.gradles!!
Completed to generate Base classes, it will added `FIXME_merge_to_build.gradle` files.
![FIXME_merge_to_build](static/fixme_merge_to_gradle.png)

Open these files and **merge to original `build.gradle` files.**

End of merge, **execute gradle sync**!!

### Use CleanArchitecture Template
Some templates need your work.

#### DataTemplateKotlin
This template create data-layer template.
![dataLayerTemplate](static/dataTemplate.png "dataTemplate")

This template will add DataSourceClass and DataRepositoryClass.

And then, please see DataSourceClass.The following notice is written there.
```
/*    FIXME MUST add below method to RepositoryModules */
//    @Binds abstract fun bindSomeDataSource(repository: SomeRepository):SomeDataSource
```

So, Copy `@Binds abstract fun bindSomeDataSource(repository: SomeRepository):SomeDataSource` to `RepositoryModules`


This Layer Provide Interface to domain.


#### DomainTemplateKotlin
This template create domain-layer template.
![domainUsecaseTemplate](static/domainUsecaseTemplate.png)

This template will add IoUsecaseClass or InputOnlyUseCaseClass or OutputOnlyUseCaseClass or SimpleUseCaseClass.

This Layer Provide Bussiness Logic and connect DataLayer to PresentationLayer.


#### PresenterActivityTemplateKotlin
This template create presenter-layer template.
![presenterActivityTemplate](static/presenterActivityTemplate.png)

This template will add ContractClass, ModuleClass, PresenterViewModelClass, ActivityClass, FragmentClass and fragment.xml.

And then, please see ModuleClass. The following notice is written there.
```
/* FIXME MUST add below method to BindingModules */
// @ContributesAndroidInjector(modules = [SomeModule::class]) @ActivityScope abstract fun contributeSomeActivityInjector(): SomeActivity
```

So, Copy `@ContributesAndroidInjector(modules = [SomeModule::class]) @ActivityScope abstract fun contributeSomeActivityInjector(): SomeActivity` to `BindingModules`.

This Layer Provides UserInterface(Activity & Fragment).
And presenterClass communicate domain-layer.

#### PresenterFragmentTemplateKotlin
This template create presenter-layer template.
![presenterFragmentTemplate](static/presenterFragmentTemplate.png)

This template will add ContractClass, PresenterViewModelClass, FragmentClass and fragment.xml.

And then, please see FragmentClass. The following notice is written there.
```
/* FIXME MUST add below method to Parent Activity's Module */
//    @Binds @IntoMap @ViewModelKey(SomePresenterViewModel::class) abstract fun bindSomePresenterViewModel(viewModel: SomePresenterViewModel): ViewModel
//    @ContributesAndroidInjector abstract fun contributeSomeFragment():SomeFragment
```

So, Copy `@Binds @IntoMap @ViewModelKey(SomePresenterViewModel::class) abstract fun bindSomePresenterViewModel(viewModel: SomePresenterViewModel): ViewModel` and `@ContributesAndroidInjector abstract fun contributeSomeFragment():SomeFragment` to `Parent activity's module`.

This Layer Provides UserInterface(Fragment).
And presenterClass communicate domain-layer.

#### PresenterServiceTemplateKotlin
This template create presenter-layer template.
![presenterServiceTemplate](static/presenterServiceTemplate.png)

This template will add ContractClass, ModuleClass, PresenterClass and ServiceClass.

And then, please see ModuleClass. The following notice is written there.
```
/* FIXME MUST add below method to BindingModules */
// @ContributesAndroidInjector(modules = [SomeServiceModule::class]) abstract fun contributeSomeServiceServiceInjector(): SomeServiceService
```

So, Copy `@ContributesAndroidInjector(modules = [SomeServiceModule::class]) abstract fun contributeSomeServiceServiceInjector(): SomeServiceService` to `BindingModules`.

This Layer Provides UserInterface(Service).
And presenterClass communicate domain-layer.

#### PresenterBroadCastReceiverTemplateKotlin
This template create presenter-layer template.
![presenterBroadCastReceiverTemplate](static/presenterBCRTemplate.png)

This template will add ContractClass, ModuleClass, PresenterClass and ReceiverClass.

And then, please see ModuleClass. The following notice is written there.
```
/* FIXME MUST add below method to BindingModules */
// @ContributesAndroidInjector(modules = [SomeReceiverModule::class]) abstract fun contributeSomeReceiverReceiverInjector(): SomeReceiverReceiver
```

So, Copy `@ContributesAndroidInjector(modules = [SomeReceiverModule::class]) abstract fun contributeSomeReceiverReceiverInjector(): SomeReceiverReceiver` to `BindingModules`.


This Layer Provides UserInterface(BroadCastReceiver).
And presenterClass communicate domain-layer.

## Example
Very simple example is in the Example folder.

## 日本語の説明
Qiitaに以下の記事を公開したのでそちらを参照

「[Kotlin用のCleanArchitectureのテンプレート作ったよ！](http://qiita.com/k_keisuke/items/38bf26e711b6918703b8)」

# Reference URL
- https://github.com/benoitletondor/Android-Studio-MVP-template
- https://github.com/android10/Android-CleanArchitecture
- https://github.com/googlesamples/android-architecture-components
- http://y-anz-m.blogspot.jp/2018/04/reified-lazy-intent-extra.html

# Licence
```
Copyright 2017- kiuchi keisuke

Licensed under the Apache License, Version 2.0 (the "License");
you may not use this file except in compliance with the License.
You may obtain a copy of the License at

   http://www.apache.org/licenses/LICENSE-2.0

Unless required by applicable law or agreed to in writing, software
distributed under the License is distributed on an "AS IS" BASIS,
WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
See the License for the specific language governing permissions and
limitations under the License.
```
