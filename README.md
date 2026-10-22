# Awesome-Graphics-APIS-SDKS

## Top Graphics APIs & SDKs Ecosystem



**Curated List of SaaS Products & Open-Source GitHub Projects**  

*Focused on GPU Memory Allocation, Frame Debugging & Real-Time Profiling*  

**Last updated: October 2026**



This repository tracks notable **SaaS platforms** and **open-source projects** for **Graphics APIs & SDKs**. These tools provide the low-level infrastructure for graphics programming—managing GPU memory, capturing frames for debugging, and profiling CPU/GPU performance—enabling developers to build efficient, correct rendering pipelines on modern explicit APIs like Vulkan and Direct3D 12.



**Examples** include Vulkan Memory Allocator, D3D12 Memory Allocator, RenderDoc, NVIDIA Nsight, PIX on Windows, AMD Radeon GPU Profiler, Intel GPA, Tracy Profiler, and Superluminal (the category leaders).



**Open-source emphasis**: This section is heavily expanded with every major active project for self-hosting, custom memory management, and transparent performance analysis—ideal for graphics engineers, engine developers, and anyone working close to the metal. The open-source landscape is anchored by **Vulkan Memory Allocator** (the de facto standard for Vulkan memory management), its **D3D12 equivalent**, and **RenderDoc** (the cross-platform frame debugger), with **Tracy** providing nanosecond-resolution profiling as a free alternative to commercial tools.



Contributions welcome! Open a PR to add/update entries. Keep descriptions factual and link to official sites.



## Table of Contents

- [SaaS/Hosted Platforms](#saas-hosted-platforms)

- [Open-Source GitHub Projects](#open-source-github-projects)

- [How to Contribute](#how-to-contribute)

- [Disclaimer](#disclaimer)



## SaaS/Hosted Platforms



- **[NVIDIA Nsight Graphics](https://developer.nvidia.com/nsight-graphics)**  

  NVIDIA's professional graphics debugging and profiling suite. Provides frame debugging, GPU trace analysis, and shader profiling with deep access to NVIDIA hardware counters. **Vendor-specific**: best results on GeForce/Quadro hardware, though debugging works on other GPUs with reduced features . Free.



- **[PIX on Windows](https://devblogs.microsoft.com/pix/)**  

  Microsoft's performance tuning and debugging tool for DirectX 12. **The best choice for D3D12** with deep Windows integration, GPU capture, memory heap analysis, and command list inspection. **DirectX only**—not useful for Vulkan workloads beyond basic counters . Free.



- **[AMD Radeon GPU Profiler (RGP)](https://gpuopen.com/rgp/)**  

  AMD's performance profiler for RDNA architecture GPUs. Visualizes wave occupancy, instruction-level timing, and hardware counters. **Vendor-specific** to AMD hardware. Free.



- **[Intel Graphics Performance Analyzers (GPA)](https://www.intel.com/content/www/us/en/developer/tools/graphics-performance-analyzers/overview.html)**  

  Intel's suite for profiling and analyzing graphics applications. Can run on non-Intel GPUs with reduced feature sets . Free.



- **[Superluminal](https://superluminal.eu/)**  

  Commercial CPU profiler for Windows with exceptional context-switch and thread-migration analysis. **Sampling-based**—no code changes required, sees all functions including third-party libraries. Windows-only. Commercial license with free trial .



## Open-Source GitHub Projects



- **[Vulkan Memory Allocator (VMA)](https://github.com/GPUOpen-LibrariesAndSDKs/VulkanMemoryAllocator)**  

  The de facto standard memory allocation library for Vulkan. Handles the complexity of explicit API memory management: allocates large memory blocks, sub-allocates them for resources, respects alignment and `bufferImageGranularity` requirements, and supports defragmentation, custom pools, and linear allocators . **Since 2017**, successfully used in projects from amateur experiments to AAA game titles across Windows, Linux, macOS, and Android . MIT licensed. Best for any Vulkan project that wants correct, efficient memory management without reimplementing the wheel.



- **[D3D12 Memory Allocator](https://github.com/GPUOpen-LibrariesAndSDKs/D3D12MemoryAllocator)**  

  The Direct3D 12 equivalent of VMA, from the same GPUOpen team. Provides `Allocator::CreateResource` as a drop-in replacement for `CreateCommittedResource`, with automatic heap tier handling, defragmentation, custom pools, statistics, and JSON dumps for visualization . **v3.0.0** released after 3+ years of development . MIT licensed. Best for D3D12 projects that need VMA-equivalent functionality with a DirectX-style API.



- **[RenderDoc](https://github.com/baldurk/renderdoc)**  

  The **cross-platform standard for frame debugging**. Captures frames from Vulkan, DirectX 11/12, OpenGL, and OpenGL ES, allowing you to inspect every resource, step through shaders, and trace the exact draw calls that affected any pixel . **No vendor lock-in**—works on NVIDIA, AMD, and Intel GPUs. Free and open-source. **Limitation**: primarily a correctness debugger, not a performance profiler—use vendor tools for hardware counters . Best for debugging rendering artifacts and verifying draw call logic on any GPU.



- **[Tracy Profiler](https://github.com/wolfpld/tracy)**  

  Real-time, nanosecond-resolution frame profiler with **MIT licensing**. Instrumentation-based (add `ZoneScoped` macros) with near-zero overhead (~50ns per zone, ~1ns for inactive zones) . **Supports GPU profiling for Vulkan, OpenGL, and D3D12** . Live streaming over network to a separate UI, frame-based statistics via `FrameMark`, lock contention detection, and memory allocation tracking . **The best free profiler available**—community consensus is that it could cost thousands and still be worth it . Best for developers who want precise, instrumented profiling of known hot paths and frame-by-frame analysis.



- **[Orbit (Google)](https://github.com/google/orbit)**  

  Sampling and dynamic instrumentation profiler for Linux and Windows. **Can attach to running processes without recompilation**—useful for profiling production builds . BSD licensed. Best for finding hotspots without code changes, especially on already-running applications.



### Additional Strong Open-Source Options



- **gfxreconstruct** — AMD's capture and replay tool for Vulkan and D3D12. Primarily for replaying captures on different hardware, useful for cross-vendor debugging .

- **AMD GPU Services (AGS)** — AMD's open-source SDK for accessing AMD-specific GPU features (FreeSync, HDR, anti-lag). Vendor-specific but open.

- **Frameworks for building custom systems**: Use **VMA** (Vulkan) or **D3D12 Memory Allocator** (DirectX) for memory management. Use **RenderDoc** for frame debugging across any GPU. Use **Tracy** for precise instrumented profiling, paired with **Orbit** or a sampling profiler to find unknown hotspots first . Use vendor tools (Nsight, RGP, PIX) only when you need hardware-specific counters that RenderDoc and Tracy cannot provide.



## How to Contribute



1. Fork the repo.

2. Add/edit entries in `README.md` (follow existing format).

3. Include: name, link, 1–2 sentence description, and whether it's SaaS or open-source.

4. Submit PR with a short explanation.



Star the repo if you find it useful!



## Disclaimer



- This is a **community-curated** list — not exhaustive and not an endorsement.

- **Vendor tools are not portable**: Nsight is best on NVIDIA, RGP on AMD, PIX on DirectX. RenderDoc is the only cross-vendor frame debugger .

- **Sampling vs instrumentation**: Sampling profilers (Superluminal, Orbit, perf) need no code changes and see everything; instrumentation profilers (Tracy) give exact per-zone timing but only for marked code. The best workflow uses both: sample to find hotspots, then instrument to understand them .

- **VMA and D3D12 Memory Allocator are libraries, not SaaS**—they are included here because they are essential open-source infrastructure for modern graphics programming, not because they have hosted offerings.



---



**Made for graphics programmers, engine developers, and anyone working with Vulkan or Direct3D 12.**  

Let's make graphics infrastructure more open, understandable, and efficient.
