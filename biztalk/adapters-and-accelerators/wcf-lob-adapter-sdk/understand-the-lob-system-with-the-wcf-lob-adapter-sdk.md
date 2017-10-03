---
title: "了解 WCF LOB 配接器 SDK 與 LOB 系統 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a0f97846-5ef2-4530-853a-fba5469156f7
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: d777022312c8511608519d155626c948da3efdb1
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="understand-the-lob-system-with-the-wcf-lob-adapter-sdk"></a>了解 LOB 系統與 WCF LOB 配接器 SDK
在開發配接器使用之前[!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]，您必須徹底了解目標的特定業務系統。 如果您不了解特定業務系統，它會公開方法，並針對安全性、 交易和其他功能提供支援的不同層級所提供的功能，您的配接器可能不會提供配接器所需的功能取用者。 本章節描述您必須了解若要有效地設計您的配接器的區域。  
  
## <a name="the-path-to-understanding"></a>要了解的路徑  
 配接器的目的是要公開資料和作業的特定業務系統以一致、 可存取的方式，根據配接器的規格和 （或） 配接器 API 所加諸的規則。 若要知道哪些作業和公開的資料，您必須了解系統的用途以及它如何公開其資料和作業。 特別是，您必須考慮下列的設計問題：  
  
-   **連接生命週期。** 連線方式開啟和關閉嗎？ 如何維護開啟的連接嗎？ 有重複使用連接的特殊需求嗎？ 如需連線的詳細資訊，請參閱`Microsoft.ServiceModel.Channels.Common.IConnection`。  
  
-   **作業和型別公開的中繼資料系統。** 特定業務系統支援作業搜尋和瀏覽和中繼資料，讓您輕鬆存取，或您必須開發支援程式碼，以提供此功能嗎？ 例如，在 SQL Server 作業是物件，例如預存程序。 有關資料行、 資料表和其他物件的型別中繼資料可輕鬆地擷取。 舊有的業務系統可能更難使用。  
  
-   **如何操作和資料會公開由系統中。** 公開 API 的方式 並封鎖 （同步） 的應用程式開發介面支援非封鎖 （非同步） 呼叫嗎？ 回呼支援？ 您將介面應用程式開發介面或通訊協定層級嗎？  
  
-   **支援的安全性、 交易和可信賴傳訊。** 如果應用程式開發介面支援這些功能，您可能想要公開至配接器取用者。 例如，SQL Server 有安全性與異動支援雖然可信賴傳訊不實用 （但會是與 MSMQ 或其他佇列的系統）。  
  
-   **哪些功能和使用方式案例很重要？** 不要限制到純技術; 了解討論和擷取與有經驗的使用者的商務需求。 有某些作業會對任何 unique 條件約束嗎？ 是否有作業尚未晦澀難懂的有用？ 某些功能很少使用為何？  
  
 若要探索這項資訊，應洽詢使用者和技術文件為目標的特定業務系統。 如果文件疏鬆或遺失，您也可以藉由查詢線上支援論壇、 線上新聞群組、 部落格，或檢查安裝檔案的實作詳細資料，深入了解系統的技術層面。 如果您有的業務開發人員或程式碼檔案的存取權，您可以找出您需要包含連接語意、 支援的安全性，以及如何操作會搜尋並叫用的資訊。  
  
## <a name="see-also"></a>另請參閱  
 [計劃和設計您的配接器使用 WCF LOB 配接器 SDK](../../adapters-and-accelerators/wcf-lob-adapter-sdk/plan-and-design-your-adapter-using-the-wcf-lob-adapter-sdk.md)   
 [使用者入門 WCF LOB 配接器 sdk](../../adapters-and-accelerators/wcf-lob-adapter-sdk/get-started-with-the-with-the-wcf-lob-adapter-sdk.md)   
 [選取適當的架構](https://msdn.microsoft.com/library/bb798089.aspx)