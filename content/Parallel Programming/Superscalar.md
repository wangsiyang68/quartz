**[Etymology](https://en.wikipedia.org/wiki/Superscalar_processor)**
Note that while scalar processors can only execute **at most one** instruction per clock cycle, a superscalar processor can execute **more than one** instruction during a clock cycle by simultaneously dispatching multiple instructions to different [execution units](https://en.wikipedia.org/wiki/Execution_unit "Execution unit") on the processor.  

![[Pasted image 20230310122110.png]]
In [Flynn's taxonomy](https://en.wikipedia.org/wiki/Flynn%27s_taxonomy "Flynn's taxonomy"), a single-core superscalar processor is classified as an [SISD](https://en.wikipedia.org/wiki/Single_instruction,_single_data "Single instruction, single data") processor (single instruction stream, single data stream), though a single-core superscalar processor that supports short vector operations could be classified as [SIMD](https://en.wikipedia.org/wiki/Single_instruction,_multiple_data "Single instruction, multiple data") (single instruction stream, multiple data streams). A [multi-core](https://en.wikipedia.org/wiki/Multi-core "Multi-core") superscalar processor is classified as an [MIMD](https://en.wikipedia.org/wiki/Multiple_instruction,_multiple_data "Multiple instruction, multiple data") processor (multiple instruction streams, multiple data streams). 

**Methodology**
A processor that dynamically finds independent instructions, and then execute them in parallel

Benefits
- No program rewrite needed

Cons
- Limits in the speedup
#pp