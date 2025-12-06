CoralNPU simulation with dsim

Prereqs: Docker available; put `AltairDSim2025.0.1_linux64.bin` and `dsim-license.json` into `dsim/`.

Build images
1) `cd dsim`
2) `docker build --platform linux/amd64 -t dsim .`
3) `cd ..`
4) `docker build --platform linux/amd64 -f utils/coralnpu.dockerfile -t coralnpu .`

Launch container
- `docker run -it --platform linux/amd64 -v $(pwd):/workspace -w /workspace coralnpu`

Compile UVM testbench (inside container)
- `cd tests/uvm`
- `make compile`

Provide program ELF
- Copy your ELF into `tests/uvm/bin`

Run a test
- `make run TEST_ELF=./bin/<test_elf_filename>`

Outputs
- Logs: `sim_work/logs/`
- Waves: `sim_work/waves/`
