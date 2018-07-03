---
title: 使用 WCF LOB 配接器 SDK 時，選取 使用的 URI 配置和定址的格式 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 3bb4feee-3d39-43ca-82ac-aba38c13bc69
caps.latest.revision: 6
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b8a9e9ffd78e0740dd366f4f09d3a832e74cda94
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37005767"
---
# <a name="select-a-uri-scheme-and-addressing-format-when-using-the-wcf-lob-adapter-sdk"></a>使用 WCF LOB 配接器 SDK 時，選取 使用的 URI 配置和定址的格式
統一資源識別元 (URI) 唯一識別資源，像是 Web 服務，或在開發配接器的情況下[!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]，連線到系統，以及要執行的動作。 本節提供有關如何建構 URI 可唯一描述端點位址和您的配接器的動作的建議。  
  
## <a name="anatomy-of-a-uri"></a>URI 的結構  
 URI 是由下列三個元件所組成：  
  
- **配置名稱**屬於 URI 字串的潛在客戶，且是第一個層級的命名結構中; 範例包括 http、 urn 中，以及 contoso。  
  
- **階層式部分**資訊，通常是階層式，而且可以包含選擇性的授權單位、 主機名稱和連接埠資訊所組成。 範例包括 www.microsoft.com 和使用者名稱 =User@microsoft.com:4099。  
  
- **查詢**包含以問號 （？） 標示，而且通常會分組為以連字號分隔的索引鍵/值組的選擇性資訊 (&)。 比方說，contoso://microsoft.com/functions?name=Find。  
  
- **片段**用以儲存配接器可能需要的額外識別資訊。 片段分隔的雜湊 （#）;比方說，contoso://microsoft.com/functions?name=Find#public。  
  
  您可能不會使用所有 URI 語法所提供的功能。  
  
## <a name="designing-the-uri"></a>設計 URI  
 身為配接器開發人員，您必須設計為目標的特定業務系統中選擇適當的 URI。 在設計您的 URI 時，務必要唯一且有意義。  
  
 唯一的 URI 是不存在的 Uri，組織內和其他企業之間以及與網際網路衝突。 例如，選擇的配置名稱，例如"http"或"afs 」 可能目前辨識，或已廣泛使用可能會導致連線 」 或 「 操作問題因為可能會將要求路由傳送至不同的系統，而非您的配接器。  
  
 URI 設計的另一個重要層面讓有意義的人員將會使用您的配接器的開發人員對象。 例如，如果您正在撰寫配接器，為醫療理賠處理系統，您可以設計包含公司名稱、 處理系統名稱 」 和 「 系統版本的目標宣告的 URI 配置： northwind.contoso.cps.v1.0://。  
  
## <a name="connecting-to-the-target-system"></a>連接到目標系統  
 連接字串具有下列語法：  
  
 **\<配置\>: //[userinfo 」\@"]\<LOB 連接字串\>**  
  
 例如，您可以連線至 contoso 目錄訂單系統 （範例企業營運應用程式） 使用下列：  
  
 **northwind.contoso.v1.0://\<servername\>嗎？類別目錄 = Contoso Integrated 的 Security = True**  
  
 您也可以提供選擇性的授權單位資訊，包括使用者名稱和密碼以及其他重要的認證之 URI 中。 不過，這可能會造成安全性風險。  
  
> [!CAUTION]
>  請勿在 URI 中傳遞使用者認證和其他機密資訊。 這項資訊可以攔截並檢視未經授權的使用者。  
  
## <a name="see-also"></a>另請參閱  
 [規劃和設計配接器使用 WCF LOB 配接器 SDK](../../adapters-and-accelerators/wcf-lob-adapter-sdk/plan-and-design-an-adapter-using-the-wcf-lob-adapter-sdk.md)