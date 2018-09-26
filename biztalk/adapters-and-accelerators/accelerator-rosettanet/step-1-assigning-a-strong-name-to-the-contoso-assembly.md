---
title: 步驟 1： 指派強式名稱給 Contoso 組件 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- private process tutorial, assigning strong-names
- strong-named assemblies
ms.assetid: c8ec4593-5a4d-47ab-8799-7b2cd3d15ffc
caps.latest.revision: 9
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 2d388fc725b8aaeec4cbfa80c23bd5e2a1b42a27
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
ms.locfileid: "25963860"
---
# <a name="step-1-assigning-a-strong-name-to-the-contoso-assembly"></a>步驟 1： 指派強式名稱給 Contoso 組件
在此步驟中，您將建立強式名稱並指派給 BizTalk 組件。 強式名稱藉由指派數位簽章和唯一的金鑰組，保證組件的唯一性。 此外，強式名稱提供完整性檢查，可保證組件的內容自上次建置以來未曾變更過。  
  
### <a name="to-create-a-strong-name-assembly-key-file"></a>建立強式名稱組件金鑰檔  
  
1.  啟動**Visual Studio 2012 的命令提示字元**。  
  
2.  在命令提示字元下，移至 Contoso 解決方案所在的位置。  
  
    > [!NOTE]
    >  根據預設，Contoso 解決方案的位置是*\<磁碟機\>*: \Documents and 設定\\*\<使用者名\>* \MyDocuments\Visual Studio\<版本\>\Projects。  
  
3.  在命令提示字元中，輸入**sn-k FabConPriceAvail.snk**，然後按下**Enter**。  
  
4.  在命令提示字元中，輸入**結束**，然後按下**Enter**。  
  
### <a name="to-assign-a-strong-name-to-your-assembly"></a>指派強式名稱給組件  
  
1.  在 [方案總管] 中，以滑鼠右鍵按一下**ContosoPriceAndAvailability**專案，然後再按一下**屬性**。  
  
2.  在 屬性頁中，按一下 **簽署**的左窗格中。  
  
3.  在右窗格中，選取**簽署組件**。  
  
4.  按一下**瀏覽**在 [選擇強式名稱金鑰檔] 欄位。  
  
5.  找出您的專案資料夾中，選取**FabConPriceAvail.snk**您稍早建立的檔案，然後按一下**開啟**。  
  
6.  按一下**確定**儲存的變更。  
  
7.  在 [方案總管] 中，以滑鼠右鍵按一下**ContosoPriceAndAvailability**專案，然後再按一下**建置**。 建置成功之後，以滑鼠右鍵按一下專案，然後**部署**。  
  
## <a name="see-also"></a>請參閱  
 [步驟 2： 為 Contoso 3A2 價格與可用性查詢/回應實例建立連接埠](step-2-create-ports-for-contoso-3a2-price-and-availability-query.md)