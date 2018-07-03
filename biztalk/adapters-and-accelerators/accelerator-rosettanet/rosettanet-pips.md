---
title: RosettaNet Pip |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- PIPs, clusters
- RosettaNet, PIPs
- PIPs, PIP specifications
- PIPs, segments
- PIPs, RosettaNet
- DTDs, DTD files
ms.assetid: 2f7e8db3-9ccb-403a-9fe7-58fbba3c4cb1
caps.latest.revision: 4
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 8891979352ce47e18c8cfda80162b3683002c6f1
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36989247"
---
# <a name="rosettanet-pips"></a>RosettaNet Pip
RosettaNet 組織建立並維護交易夥伴介面處理程序 (PIP) 以為所有 RosettaNet 訊息交換提供一般商務處理程序定義。  
  
 每個 PIP 規格都提供了文件類型定義 (DTD) 檔案以及訊息指導方針文件。 DTD 檔案定義服務內容訊息結構。 訊息指導方針文件是可以閱讀的 HTML 檔案，其中指定元素階層條件約束。 這兩者一起提供完整的商務程序定義。  
  
 如需有關 PIP 規格的詳細資訊，請參閱 RosettaNet 網站，網址[ http://go.microsoft.com/FWLink/?LinkID=33859 ](http://go.microsoft.com/FWLink/?LinkID=33859)。  
  
## <a name="pip-contents"></a>PIP 內容  
 PIP 規格執行下列動作：  
  
- 描述實作的公開程序模式  
  
- 描述設定公開程序的方法  
  
- 提供在 PIP 之內交換的文件參照。  
  
  PIP 規格包含三個主要部分： 商務營運檢視 (BOV)、 功能服務檢視 (FSV) 以及實作架構檢視 (IFV)。 每個檢視都會指定元素階層條件約束：  
  
- BOV 指定商務資料實體及商務程序流程的語意， 描述開始和結束狀態，以及交易夥伴角色。 並描述角色之間的互動，以及安全性、稽核和程序控制的詳細資訊。 它指定商務文件及商務資料實體。  
  
- FSV 指定網路元件服務、代理程式以及互動， 提供執行 PIP 所需的網路元件設計，並描述可能的網路元件互動。  
  
- IFV 指定執行 PIP 所需的網路通訊協定訊息格式和通訊需求。  
  
## <a name="clusters-and-segments"></a>叢集與區段  
 您可以依照高層級商務功能 (叢集) 和副功能 (區段) 區分 PIP。 叢集和區段會將商務訊息組織成可辨識的類別。 下表列出這些叢集和區段。  
  
|Clusters|區段|  
|--------------|--------------|  
|0: RosettaNet 支援|0A： 系統管理<br /><br /> 0c： 測試|  
|1： 夥伴產品 & 服務重新檢視|1A： 合作夥伴檢閱<br /><br /> 1B： 產品 & 服務重新檢視|  
|2： 產品資訊|2A： 散佈準備<br /><br /> 2B： 產品變更通知<br /><br /> 2c： 產品設計資訊<br /><br /> 2D： 共同作業的設計與工程|  
|3： 訂單管理|3A: Quote & 訂購項目<br /><br /> 3B： 傳輸與通訊群組<br /><br /> 3c： 傳回與財務<br /><br /> 3D： 產品組態|  
|4： 庫存管理|4A： 共同作業趨勢預測<br /><br /> 4B： 清查配置<br /><br /> 4 C： 清查和報告<br /><br /> 4d： 存貨補充<br /><br /> 4E： 銷售報告<br /><br /> 4F： 價格保護|  
|5： 行銷資訊管理|5A： 領先機會管理<br /><br /> 5B： 行銷活動管理|  
|6： 服務及支援中心|6A： 提供以及管理員保證、 服務套件、 以及合約服務<br /><br /> 6B： 提供以及管理員資產管理 （與 6A 合併）<br /><br /> 6c： 技術支援和服務管理|  
|7： 製造|7A： 設計傳輸<br /><br /> 7B： 管理製造 WO 和 WIP<br /><br /> 7c： 散佈製造資訊|  
  
 每個區段都包含數個特定的訊息 PIP。 例如，3A4 PIP 屬於「訂單管理」叢集 (叢集 3) 和「報價及訂單輸入」區段 (叢集 3 的區段 A)。 這個區段包含其他相關的訊息 PIP，如下所示：  
  
 叢集 3： 訂單管理  
  
-   區段 a: Quote 及排列項目  
  
    -   PIP 3A1： 要求報價  
  
    -   PIP 3A2： 要求價格與可用性  
  
    -   PIP 3A3： 要求購物車轉移  
  
    -   PIP 3A4： 管理訂單  
  
    -   PIP 3A5： 查詢訂單狀態  
  
    -   PIP 3A6： 散佈訂單狀態  
  
    -   …  
  
## <a name="see-also"></a>另請參閱  
 [RosettaNet 與 CIDX 訊息標準](../../adapters-and-accelerators/accelerator-rosettanet/rosettanet-and-cidx-messaging-standards.md)   
 [RNIF 標準](../../adapters-and-accelerators/accelerator-rosettanet/rnif-standard.md)