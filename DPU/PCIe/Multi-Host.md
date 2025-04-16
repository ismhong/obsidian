PCIe Multi-Host技術是一種允許多個主機系統共享一個PCIe設備的解決方案，它透過不同的實現方式來滿足各種應用場景的需求。以下是PCIe Multi-Host技術的主要實現方式及其特點：

1. 通過PCIe Fabric
- 連接方式：通過PCIe Fabric，多個主機與末端點（EP）通過物理路徑相連。
- 技術支援：Broadcom（PLX）和Microchip（Microsemi）等PCIe SW廠家支持Fabric模式，通過韌體配置複雜的PCIe拓撲。
- 可靠性：可實現多PCIe switch互連，形成複雜可靠的網路。
- 優勢：靈活性高，支持多種設備共享，如NVMe、GPU或網卡。
- 成本：相對較高。

2. 透過網路
- 基礎架構：利用現有的Eth網路架構，實現Multi-Host。
- 範例：Intel的FM10000晶片，對外提供PCIe信號，內部轉換為網路信號，實現IO共享。
- 優勢：復用現有網路技術，成熟且靈活。

3. 透過NIC（網路介面卡）
- 技術特性：某些高級NIC晶片如Broadcom和Mellanox的NIC支持Multi-Host。
- 範例：Mellanox ConnectX-4/5，PCIe介面可分成4個獨立介面連接4個CPU。
- 優勢：經濟，省去Switch晶片，但連接主機數量有限。

4. PCIe Switch Adapter
- 具體產品：如DiLiVing的LRNV9324-4I，採用PLX PEX8724主控。
- 功能：提供PCIe3.0 x8頻寬，連接多個SFF-8643介面的SSD，支持Multi-Host模式。
- 特點：支持1+1或N+1主機冗餘，低延遲數據傳輸，適合高可用性系統。
- 應用：除直連SSD，還可用於擴展連接顯示卡，實現多顯示卡拼接或挖礦。

5. Multi-root I/O Virtualization (MR-IOV)
- 定義：允許多個根端系統共享單個PCIe設備。
- 實現：通過配置 PCIe switch，允許多個主機訪問同一設備，如 NVMe SSD。
- 動態分配：支持頻寬和資源的動態分配，提高系統靈活性和效率。

6. Virtual Switch/Switch Partitioning
- 定義：將物理PCIe Switch分成多個Virtual Switch，實現多個Host共用一個Switch。
- 特點：Virtual Switch之間互不干擾，支持動態分配頻寬和資源。


## 總結
PCIe Multi-Host技術透過多種實現方式，提供了靈活、高效的多主機共享PCIe設備的解決方案。PCIe Fabric方式最為靈活但成本較高，網路方式成熟且經濟，NIC方式經濟但連接主機數量有限。此外，PCIe Switch Adapter、MR-IOV、P2P、Virtual Switch、NTB和PCIe Bridge等技術的引入，進一步豐富了PCIe Multi-Host的實現手段，滿足了不同場景下的需求。