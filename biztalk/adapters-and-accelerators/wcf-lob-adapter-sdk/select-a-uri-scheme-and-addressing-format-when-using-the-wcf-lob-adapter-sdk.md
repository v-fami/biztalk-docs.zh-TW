---
title: "使用 WCF LOB 配接器 SDK 時，選取 使用 URI 配置和定址的格式 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3bb4feee-3d39-43ca-82ac-aba38c13bc69
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 6df8145fac74761fee4aabd34ff01d708b646c12
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="select-a-uri-scheme-and-addressing-format-when-using-the-wcf-lob-adapter-sdk"></a>使用 WCF LOB 配接器 SDK 時，選取 使用 URI 配置和定址的格式
統一資源識別元 (URI) 可唯一識別資源，像是 Web 服務，或在使用開發配接器的情況下[!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]，連接到系統，以及要執行的動作。 本節提供的建議如何建構 URI 來唯一描述的端點位址以及您的配接器的動作。  
  
## <a name="anatomy-of-a-uri"></a>URI 的剖析  
 URI 是由下列三個元件所組成：  
  
-   **配置名稱**URI 字串的前置部分，而命名的結構; 第一個層級範例包括 http、 urn 和 contoso。  
  
-   **階層式部分**包含通常階層，而且可以包含選擇性的授權單位、 主機名稱和連接埠資訊的資訊。 範例包括 www.microsoft.com 和使用者名稱 =User@microsoft.com:4099。  
  
-   **查詢**包含以問號 （？） 標示，而且通常會分組為索引鍵/值組，以連字號分隔的選擇性資訊 (&)。 例如，contoso://microsoft.com/functions?name=Find。  
  
-   **片段**用來儲存配接器可能需要的額外識別資訊。 片段隔開雜湊 （#）。例如，contoso://microsoft.com/functions?name=Find#public。  
  
 您可能不會使用所有的 URI 語法所提供的功能。  
  
## <a name="designing-the-uri"></a>設計 URI  
 身為配接器開發人員，您必須設定適當的 URI 為目標的特定業務系統。 在設計您的 URI 時，務必要唯一且具有意義。  
  
 唯一的 URI 是未與現有的 Uri，在組織內外的其他企業網路和網際網路衝突。 例如，選擇的配置名稱，例如"http"或"afs 」 可能目前辨識，或已廣為使用可能會導致連接或操作問題因為要求可能會被路由至不同系統而非您的配接器。  
  
 URI 設計的另一個重要層面對它有意義的人員將會使用您的配接器的開發人員對象。 例如，如果您要撰寫配接器的醫療理賠處理系統，您可以設計包含公司名稱、 處理系統名稱和作業系統版本的目標宣告的 URI 配置： northwind.contoso.cps.v1.0://。  
  
## <a name="connecting-to-the-target-system"></a>連接到目標系統  
 連接字串具有下列語法：  
  
 **\<配置 >: //[userinfo"@"]\<LOB 連接字串 >**  
  
 比方說，您無法連接到 contoso 目錄排序 system （企業營運應用程式的範例行） 使用下列：  
  
 **northwind.contoso.v1.0://\<伺服器名稱 >？目錄 Contoso 與整合式的安全性 = = True**  
  
 您也可以提供選擇性的授權單位 URI，包括使用者名稱和密碼以及其他重要的認證資訊。 不過，這可能會造成安全性風險。  
  
> [!CAUTION]
>  請勿在 URI 中傳遞使用者認證和其他機密資訊。 無法攔截與未經授權的使用者檢視這項資訊。  
  
## <a name="see-also"></a>另請參閱  
 [計劃和設計配接器使用 WCF LOB 配接器 SDK](../../adapters-and-accelerators/wcf-lob-adapter-sdk/plan-and-design-an-adapter-using-the-wcf-lob-adapter-sdk.md)