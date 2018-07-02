---
title: 解除部署其他教學課程專案 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 5fce837f-1853-4d5d-a680-8ae2a974c750
caps.latest.revision: 5
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e2c014a094acac4e374605cd0ebd9b9c50c9d733
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36976279"
---
# <a name="undeploy-other-tutorial-projects"></a>解除部署其他教學課程專案
當您部署 BizTalk Accelerator for HL7 ([!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]) 教學課程中，[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]教學課程的組件會將檔案儲存在組態資料庫 （也稱為 「 BizTalk 管理資料庫） 和全域組件快取中。 如果您已執行另一個[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]教學課程，以及部署在該教學課程中所建立的組件，您可能會發生錯誤時在批次處理教學課程中的三個部分中測試您的組件。 這可能是因為您只可以一次部署一個訊息結構描述。  
  
 您可以避免這些錯誤，供您在先前的教學課程中部署的解除部署組件。 如有需要您可以重新部署組件更新版本。  
  
 之前解除部署組件，您必須取消登錄組件中的協調流程。 您也需要移除任何您想要解除部署，從其他任何您想要保留已部署的組件的組件的參考。 替代方式是刪除開始另一個教學課程之前，一個教學課程中，與相關聯的所有 Dll。  
  
### <a name="to-undeploy-an-assembly"></a>若要解除部署組件  
  
1. 取消登錄協調流程用於您想要藉由按一下 BizTalk 總管 中的 Visual Studio 中的協調流程，然後按一下 解除部署組件**取消登錄**。  
  
2. 您想要保留已部署的任何組件中移除您想要解除部署組件的參考。 以滑鼠右鍵按一下方案總管 中的參考，然後按一下**移除**。  
  
3. 開啟 BizTalk 總管 中，以滑鼠右鍵按一下您想要解除部署，然後按一下 組件**Undeploy**。  
  
   如需有關解除部署組件的詳細資訊，請參閱 「 解除部署組件使用 BizTalk 總管 」 在 BizTalk Server 說明中。  
  
## <a name="see-also"></a>另請參閱  
 [準備使用批次處理教學課程](../../adapters-and-accelerators/accelerator-hl7/preparing-to-use-the-batching-tutorial.md)