# Setup Guide

Provides a step-by-step guide to setup Oceanology requirments. If you need help adding Oceanology to your scene after all requirements have been configured video here [TODO VIDEO] 

!!! note

    Before integrating Oceanology into your main project, generating a test project is recommended.

Before jumping into it lets create a new Unreal third person sample project. You may name it what you wish.

<figure markdown="span">
  ![step-4](../assets/images/step-4.jpg)
  <figcaption>Lets create a test project. Next we have to update the defaultengine.ini file.</figcaption>
</figure>

<figure markdown="span">
  ![step-5](../assets/images/step-5.jpg)
  <figcaption>Navigate to file explorer and find your project root</figcaption>
</figure>

<figure markdown="span">
  ![step-6](../assets/images/step-6.jpg)
  <figcaption>Open Config folder and open DefaultEngine.ini.</figcaption>
</figure>

<figure markdown="span">
  ![step-7](../assets/images/step-7.jpg)
  <figcaption>Find Engine.RendererSettings section and update it as following</figcaption>
</figure>

---

### DefaultEngine.ini

These settings are important to make sure that your render settings play nice with oceanology. Feel free to merge your custom settings with the requirments below but keep in mind we can't test all settings so if you experience issues feel free to head over to our discord community.

!!! note

    Important code may vary depending on the version of the engine. This code is used to correct rendering problems, such as strange artifacts and blinking when moving a plane. Add under the section `[/Script/Engine.RendererSettings]` below the default settings in `project/config/defaultengine.ini`

Open `defaultengine.ini` and look for `[/Script/Engine.RendererSettings]` looks approximately like:

``` ini

[/Script/Engine.RendererSettings]
r.ReflectionMethod=1
r.GenerateMeshDistanceFields=True
r.DynamicGlobalIlluminationMethod=1
r.Lumen.TraceMeshSDFs=0
r.Shadow.Virtual.Enable=1
r.Mobile.EnableNoPrecomputedLightingCSMShader=1
r.DefaultFeature.AutoExposure.ExtendDefaultLuminanceRange=True
r.DefaultFeature.AutoExposure.ExtendDefaultLuminanceRange=true

r.DefaultFeature.LocalExposure.HighlightContrastScale=0.8

r.DefaultFeature.LocalExposure.ShadowContrastScale=0.8

```

Now add:

``` ini
;Lighting
r.SupportStationarySkylight=False
r.SupportLowQualityLightmaps=False
r.Mobile.EnableStaticAndCSMShadowReceivers=False
r.Mobile.AllowDistanceFieldShadows=False
r.DefaultBackBufferPixelFormat=4

;Optimized
r.optimizedWPO=1

;AntiAliang
r.AntiAliasingMethod=4
r.MSAACount=4
r.TSR.AsyncCompute=3

;MotionBlur
r.DefaultFeature.MotionBlur=False

;Velocity
r.VelocityOutputPass=2

;Shadow.Virtual
r.Shadow.Virtual.NonNanite.IncludeInCoarsePages=0
r.Shadow.Virtual.ForceOnlyVirtualShadowMaps=1
r.Shadow.Virtual.TranslucentQuality=0
r.Shadow.Virtual.Cache.DrawInvalidatingBounds=1
r.Shadow.Virtual.Cache.StaticSeparate=1
r.UseClusteredDeferredShading=1
r.Shadow.Virtual.OnePassProjection=1
r.Shadow.Virtual.NormalBias=1
r.Shadow.Virtual.ForceOnlyVirtualShadowMaps=1

;Distance Fields
r.DistanceFields.MaxPerMeshResolution=256
r.DistanceFields.SupportEvenIfHardwareRayTracingSupported=0

;SkinCache
r.SkinCache.MemoryLimitForBatchedRayTracingGeometryUpdates=128
r.SkinCache.MaxRayTracingPrimitivesPerCmdList=1000000
r.SkinCache.MaxDispatchesPerCmdList=1000
r.SkinCache.AllowDupedVertsForRecomputeTangents=1
r.SkinCache.RecomputeTangentsParallelDispatch=1
r.SkinCache.SceneMemoryLimitInMB=148
r.SkinCache.CompileShaders=True
r.SkinCache.DefaultBehavior=0

;GPU SkinCache
r.GPUSkin.Support16BitBoneIndex=True
r.GPUSkin.UnlimitedBoneInfluences=True
r.GBufferDiffuseSampleOcclusion=1

;Lumen
r.Lumen.ScreenProbeGather.ScreenTraces.HZBTraversal.UncertainTraceRelativeDepthThreshold=.02
r.Lumen.ScreenProbeGather.ScreenSpaceBentNormal.ApplyDuringIntegration=0
r.Lumen.Tracing.MaxTraceDistance=20000
r.LumenScene.SurfaceCache.MeshCardsMergedResolutionScale=1
r.LumenScene.SurfaceCache.MeshCardsMaxLOD=0
r.LumenScene.DirectLighting.OffscreenShadowing.TraceMeshSDFs=0
r.Lumen.HardwareRayTracing=1
r.Lumen.TranslucencyVolume.TraceFromVolume=1
r.Lumen.Reflections.RadianceCache=1
r.LumenScene.Radiosity.ProbeOcclusion=0
r.LumenScene.FarField=1
r.LumenScene.FarField.MaxTraceDistance=100000
r.Lumen.HardwareRayTracing.MaxIterations=128
r.Lumen.TraceMeshSDFs=0
r.Lumen.SampleFog=0
r.Lumen.Reflections.Contrast=0.75
r.Lumen.TranslucencyReflections.FrontLayer.EnableForProject=True

;ShadingRejection
r.TSR.History.SampleCount=32
r.TSR.ShadingRejection.Flickering.FrameRateCap=30
r.TSR.ShadingRejection.Flickering.MaxParralaxVelocity=2
r.TSR.ShadingRejection.Flickering.Period=3

;World Partition
wp.Runtime.RuntimeSpatialHashUseAlignedGridLevels=0
wp.Runtime.RuntimeSpatialHashSnapNonAlignedGridLevelsToLowerLevels=0
wp.Runtime.RuntimeSpatialHashPlaceSmallActorsUsingLocation=1
wp.Runtime.RuntimeSpatialHashPlacePartitionActorsUsingLocation=0

;Texture Streaming
r.Streaming.PoolSize=8000
r.MeshStreaming=True

;Occlusion
r.NumBufferedOcclusionQueries=2
r.InstanceCulling.OcclusionCull=1
;LevelStreaming
s.LevelStreamingActorsUpdateTimeLimit=10
s.UnregisterComponentsTimeLimit=5

;Nanite
r.Nanite.Streaming.Imposters=0
r.Nanite.CoarseMeshStreaming=True
r.Nanite.ProxyRenderMode=2
r.Nanite.Streaming.NumInitialRootPages=6144
r.Nanite.MaxNodes=2621440

;Shaders
r.Shaders.RemoveDeadCode=1

;GPU scene
r.GPUScene.ParallelUpdate=1

;Virtual Texture
r.VirtualTextures=True
r.VirtualTexturedLightmaps=True
bEnableVirtualTextureOpacityMask=True
r.VT.MaxUploadsPerFrame=500
r.VT.MaxUploadsPerFrameInEditor=1000
r.VT.MaxTilesProducedPerFrame=100
r.VT.MaxReleasedPerFrame=5
r.VT.NumGatherTasks=6
r.VT.SyncProduceLockedTiles=0
r.VT.IOPriority_HighPagePri=4
r.VT.CsvStats=2

[/Script/Engine.VirtualTexturePoolConfig]
+Pools=(Formats=(PF_DXT1), SizeInMegabyte=120,  bAllowSizeScale=True, MinScaledSizeInMegabyte=37, bEnableResidencyMipMapBias=True)
+Pools=(Formats=(PF_DXT5), SizeInMegabyte=37,  bAllowSizeScale=True, MinScaledSizeInMegabyte=8, bEnableResidencyMipMapBias=True)
+Pools=(Formats=(PF_BC4),  SizeInMegabyte=37,  bAllowSizeScale=True, MinScaledSizeInMegabyte=16, bEnableResidencyMipMapBias=True)
+Pools=(Formats=(PF_BC5),  SizeInMegabyte=72,  bAllowSizeScale=True, MinScaledSizeInMegabyte=16, bEnableResidencyMipMapBias=True)
+Pools=(Formats=(PF_BC6H), SizeInMegabyte=60,  bAllowSizeScale=True, MinScaledSizeInMegabyte=30, bEnableResidencyMipMapBias=True)
+Pools=(Formats=(PF_BC7),  SizeInMegabyte=72, bAllowSizeScale=True, MinScaledSizeInMegabyte=37 bEnableResidencyMipMapBias=True)
+Pools=(Formats=(PF_G8),  SizeInMegabyte=200, bAllowSizeScale=True, MinScaledSizeInMegabyte=70 bEnableResidencyMipMapBias=True)
+Pools=(SizeInMegabyte=64, bAllowSizeScale=False, bEnableResidencyMipMapBias=False)

;NVidia DLSS
r.Streamline.DLSSG.Enable=1
r.NGX.DLSS.WaterReflections.TemporalAA=1
[/Script/DLSS.DLSSSettings]
bEnableDLSSInEditorViewports=True

```

Next open your project you created above from the launcher and navigate to the plugins settings

---

<figure markdown="span">
  ![step-9](../assets/images/step-9.jpg)
  <figcaption>Navigate to the plugin settings</figcaption>
</figure>

<figure markdown="span">
  ![step-10](../assets/images/step-10.jpg)
  <figcaption>Look for the Oceanology and enable it</figcaption>
</figure>

<figure markdown="span">
  ![step-11](../assets/images/step-11.jpg)
  <figcaption>Restart when prompted</figcaption>
</figure>

<figure markdown="span">
  ![step-12](../assets/images/step-12.jpg)
  <figcaption>Enable plugin content visibility as these may be hidden by default.</figcaption>
</figure>

<figure markdown="span">
  ![step-13](../assets/images/step-13.jpg)
  <figcaption>Navigate to plugin content for demo levels and files</figcaption>
</figure>
