---
title: "解除部署其他教學課程專案 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5fce837f-1853-4d5d-a680-8ae2a974c750
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 1e5c4d7e20fc4d8e7c8bea724625dde770b4aca2
ms.sourcegitcommit: 3fc338e52d5dbca2c3ea1685a2faafc7582fe23a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/01/2017
---
# <a name="undeploy-other-tutorial-projects"></a>解除部署其他教學課程專案
當您部署 BizTalk Accelerator for HL7 ([!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]) 教學課程，[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]教學課程的組件檔案儲存在組態資料庫 （也稱為 「 BizTalk 管理資料庫） 和全域組件快取。 如果您已執行另一個[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]教學課程，以及部署在該教學課程中所建立的組件，您可以測試組件中批次處理教學課程的三個部分時，會發生錯誤。 這可能是因為您只可以一次部署一個訊息結構描述。  
  
 您可以避免這些錯誤，供您在先前的教學課程中部署的解除部署組件。 如有需要您可以重新部署組件更新版本。  
  
 之前解除部署組件，您必須取消登錄協調流程組件中。 您也需要移除任何您想要從其他任何您想要保留已部署的組件解除部署組件的參考。 替代方法是刪除相關聯一個教學課程中，再啟動另一個教學課程的所有 Dll。  
  
### <a name="to-undeploy-an-assembly"></a>若要解除部署組件  
  
1.  取消登錄協調流程中您想要按一下 BizTalk 總管 中的 Visual Studio 中的協調流程，然後按一下 解除部署組件使用**取消登錄**。  
  
2.  在您想要保留已部署的任何組件，會移除您想要解除部署組件的參考。 以滑鼠右鍵按一下方案總管 中的參考，然後按一下**移除**。  
  
3.  開啟 BizTalk 總管 中，以滑鼠右鍵按一下您想要解除部署，然後按一下 組件**解除部署**。  
  
 如需有關解除部署組件的詳細資訊，請參閱 「 解除部署組件使用 BizTalk 總管 」 在 BizTalk Server 說明中。  
  
## <a name="see-also"></a>請參閱  
 [準備使用批次處理教學課程](../../adapters-and-accelerators/accelerator-hl7/preparing-to-use-the-batching-tutorial.md)