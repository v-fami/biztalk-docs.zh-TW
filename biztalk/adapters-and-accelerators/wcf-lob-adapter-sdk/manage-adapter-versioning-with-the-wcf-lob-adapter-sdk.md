---
title: 管理配接器使用 WCF LOB 配接器 SDK 進行版本控制 |Microsoft Docs
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
ms.openlocfilehash: 8dfb323bf810f69c8a8f1f857b0d0240c14c4d18
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36975183"
---
# <a name="manage-adapter-versioning-with-the-wcf-lob-adapter-sdk"></a>管理配接器使用 WCF LOB 配接器 SDK 進行版本控制
初始部署後的配接器和潛在進行數次在其存留期期間，配接器 （和它們所公開的端點） 可能需要針對各種原因而變更。 這些原因，包括變更商務需求、 資訊技術需求或商務系統的配接器本身的一行的問題。 本主題討論不同的策略來處理使用撰寫配接器的版本控制[!INCLUDE[afproductnamelong](../../includes/afproductnamelong-md.md)]。  
  
## <a name="versioning-and-windows-communication-foundation"></a>版本控制和 Windows Communication Foundation  
 [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]建置於[!INCLUDE[firstref_btsWinCommFoundation](../../includes/firstref-btswincommfoundation-md.md)]而且依賴其基礎結構系統之間交換訊息。 使用的機制，[!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)]公開 （expose)，您可以版本服務與資料合約。 如需詳細資訊，包括最佳作法服務版本設定，請參閱[服務版本設定](http://go.microsoft.com/fwlink/?LinkId=85497)在[!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)]線上參考。 如需詳細資訊，包括最佳作法資料合約版本控制，請參閱[資料合約版本控制](http://go.microsoft.com/fwlink/?LinkId=120177)在[!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)]線上參考。  
  
## <a name="versioning-scenarios"></a>版本設定案例  
 有兩種主要的版本控制案例：  
  
- 一個配接器版本支援目標系統的多個的版本。  
  
- 兩個或多個配接器版本支援在相同的系統或兩個或多個不同的系統。  
  
  您可能也需要釋放您的配接器的新版本，如果更新[!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]會影響現有的功能。  
  
  每個案例都需要不同的版本控制策略。  
  
> [!NOTE]
>  [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]不會強制使用任何特定的版本控制案例。 它會保留給開發人員決定配接器的版本控制需求。  
  
### <a name="one-adapter-supports-multiple-versions-of-target-system"></a>一張介面卡支援多種版本的目標系統  
 當配接器支援多個版本的目標系統時，您應該公開一或多個繫結屬性，可用來識別所需的版本。 例如，配接器可能支援多個目標系統的廠商所提供的通訊程式庫。 使用名為"LibraryVersion 」 的自訂繫結屬性，配接器取用者可以選擇使用哪一個程式庫基礎的部署環境或其他需求。  
  
### <a name="two-or-more-adapters-support-one-version-of-target-system"></a>兩個或多個配接器支援目標系統的一個的版本  
 在此情況下，每個配接器應該使用唯一的配置 (ContosoV1: / / 和 ContosoV2: / /) 和唯一的繫結名稱 （ContosoV1Binding 和 ContosoV2Binding）。 廠商應該考慮使用中的配置和繫結名稱 （例如 Microsoft.ContosoV1:// 和 Microsoft.ContosoV1Binding） 及其名稱。  
  
### <a name="new-versions-of-the-wcf-lob-adapter-sdk"></a>WCF LOB 配接器 SDK 的新版本  
 當新版[!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]會發行，您將能夠安裝新版本，而不必重新編譯您的配接器，因為[!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]發行都可以與舊版相容。 不過，您應該評估新的版本，以判斷是否有所變更的功能，取決於您的配接器，或者如果沒有會受益於您的配接器實作的新功能。  
  
## <a name="see-also"></a>另請參閱  
 [使用 WCF LOB 配接器 SDK 開發最佳做法](../../adapters-and-accelerators/wcf-lob-adapter-sdk/development-best-practices-using-the-wcf-lob-adapter-sdk.md)