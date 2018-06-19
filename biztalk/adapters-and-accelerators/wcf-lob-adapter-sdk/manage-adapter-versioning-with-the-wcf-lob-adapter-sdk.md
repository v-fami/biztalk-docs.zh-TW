---
title: 管理配接器使用 WCF LOB 配接器 SDK 進行版本控制 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: fb596fdd-251c-4978-9f33-cf2883d281d8
caps.latest.revision: 15
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: bf8d5d13c37f683a118484c9c08fa90c13a95533
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22225830"
---
# <a name="manage-adapter-versioning-with-the-wcf-lob-adapter-sdk"></a>管理配接器使用 WCF LOB 配接器 SDK 進行版本控制
初始部署之後的配接器和潛在進行數次存留期間，配接器 （和它們所公開的端點） 可能需要針對各種原因而變更。 這些原因，包括變更商務需要、 資訊技術需求或問題商務系統或配接器本身的列。 本主題討論不同的策略來處理使用撰寫的配接器的版本控制[!INCLUDE[afproductnamelong](../../includes/afproductnamelong-md.md)]。  
  
## <a name="versioning-and-windows-communication-foundation"></a>版本控制和 Windows Communication Foundation  
 [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]建置於[!INCLUDE[firstref_btsWinCommFoundation](../../includes/firstref-btswincommfoundation-md.md)]，並依賴它的基礎結構系統之間交換訊息。 使用機制，[!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)]公開，您可以版本服務與資料合約。 如需詳細資訊，包括服務版本控制的最佳作法，請參閱[服務版本控制](http://go.microsoft.com/fwlink/?LinkId=85497)中[!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)]線上參考。 如需詳細資訊，包括的資料合約版本控制，最佳作法，請參閱[資料合約版本控制](http://go.microsoft.com/fwlink/?LinkId=120177)中[!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)]線上參考。  
  
## <a name="versioning-scenarios"></a>版本控制案例  
 有兩種主要的版本設定案例：  
  
-   一個配接器版本支援多個版本的目標系統。  
  
-   兩個或多個配接器版本支援在相同的系統或兩個或多個不同的系統。  
  
 您可能也需要發行您的配接器的新版本，如果更新[!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]會影響現有的功能。  
  
 每個案例都需要不同的版本控制策略。  
  
> [!NOTE]
>  [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]不強制任何特定的版本控制案例。 它會保持到開發人員決定配接器的版本控制需求。  
  
### <a name="one-adapter-supports-multiple-versions-of-target-system"></a>一張介面卡支援多種版本的目標系統  
 當配接器支援多個版本的目標系統時，您應該公開一或多個繫結屬性可以用來識別所需的版本。 例如，配接器可支援多個目標系統的廠商所提供的通訊程式庫。 使用名為"LibraryVersion"的自訂繫結屬性，配接器取用者可以選擇要使用哪一個程式庫為基礎的部署環境或其他需求。  
  
### <a name="two-or-more-adapters-support-one-version-of-target-system"></a>兩個或多個配接器支援目標系統的一個的版本  
 在此情況下，每個配接器應該使用自己的配置 (ContosoV1: / / 和 ContosoV2: / /) 和唯一的繫結名稱 （ContosoV1Binding 和 ContosoV2Binding）。 廠商應該考慮使用中的配置和繫結名稱 （例如，Microsoft.ContosoV1:// 和 Microsoft.ContosoV1Binding） 及其名稱。  
  
### <a name="new-versions-of-the-wcf-lob-adapter-sdk"></a>WCF LOB Adapter SDK 的新版本  
 當新版本的[!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]會釋出，您將能夠不需要重新編譯您的配接器，因為安裝新版本[!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]版本都具有回溯相容性。 不過，您應該評估新的版本，來判斷是否已變更的功能，取決於您的配接器，或如果沒有將受益於您的配接器實作的新功能。  
  
## <a name="see-also"></a>另請參閱  
 [使用 WCF LOB 配接器 SDK 開發最佳作法](../../adapters-and-accelerators/wcf-lob-adapter-sdk/development-best-practices-using-the-wcf-lob-adapter-sdk.md)