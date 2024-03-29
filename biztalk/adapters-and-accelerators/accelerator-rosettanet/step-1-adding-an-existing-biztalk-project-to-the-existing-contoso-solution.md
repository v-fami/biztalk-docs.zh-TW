---
title: 步驟 1： 將現有的 BizTalk 專案新增至現有的 Contoso 解決方案 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- projects, adding to solutions
- private process tutorial, adding projects to solutions
ms.assetid: 9e84d282-01aa-4611-8462-c1acef234042
caps.latest.revision: 6
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 9491c52bfbcbc78e2897cf509b1be320bb223e19
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37010239"
---
# <a name="step-1-adding-an-existing-biztalk-project-to-the-existing-contoso-solution"></a>步驟 1： 將現有的 BizTalk 專案新增至現有的 Contoso 解決方案
The Microsoft® [!INCLUDE[BTARN_CurrentVersion_FirstRef](../../includes/btarn-currentversion-firstref-md.md)] SDK 包含私用程序協調流程做為不錯的起點，當您自己的私用程序。 在此步驟中，您要將該協調流程加入至您的方案，並將變更組件名稱，以免與 [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] 在安裝期間所安裝的 PrivateResponder 協調流程發生衝突。 在開始之前，開啟您在中建立的 Contoso 解決方案[步驟 1： 為 Contoso 價格與可用性要求建立新的 BizTalk 解決方案](../../adapters-and-accelerators/accelerator-rosettanet/step-1-create-new-biztalk-solution-for-contoso-price-and-availability-request.md)。  
  
### <a name="to-add-the-privateresponder-project-to-the-contoso-solution"></a>將 PrivateResponder 專案加入至 Contoso 解決方案  
  
1.  將 PrivateResponder SDK 範例複製至 Contoso 解決方案資料夾。  
  
    > [!NOTE]
    >  根據預設，PrivateResponder SDK 範例位於 C:\Program Files\Microsoft BizTalk\<版本\>Accelerator for RosettaNet\SDK\PrivateResponder 資料夾。  
  
2.  在 Visual Studio 中，按一下**檔案**，指向**新增**，然後按一下**現有專案**。  
  
3.  在 [加入現有專案] 對話方塊中，找出您的方案，選取資料夾**PrivateResponder.btproj**專案檔案，然後按一下**開啟**。  
  
### <a name="to-change-the-privateresponder-assembly-name-and-default-namespace"></a>變更 PrivateResponder 組件名稱及預設命名空間  
  
1.  在 [方案總管] 中，以滑鼠右鍵按一下**PrivateResponder**專案，然後再按一下**屬性**。  
  
2.  在 [PrivateResponder 屬性頁] 對話方塊的主控台樹狀目錄中，按一下**一般**。 在 [詳細資料] 窗格中，在**組件名稱**方塊中，輸入**ContosoPriceAndAvailability.PrivateResponder**。  
  
3.  在 **預設命名空間**方塊中，輸入**ContosoPriceAndAvailability**。  
  
4.  按一下 **確定**以關閉 PrivateResponder 屬性頁 對話方塊。  
  
5.  在 [方案總管] 中，按兩下**PrivateResponder.odx**。  
  
6.  在 [**協調流程檢視**] 視窗中，確定**協調流程屬性**(下**PrivateResponderProcess**) 已選取。  
  
7.  在 **屬性**視窗，請在**命名空間**欄位中，輸入**ContosoPriceAndAvailability**，然後按**Enter**。  
  
## <a name="see-also"></a>另請參閱  
 [步驟 2：定義與發佈 Contoso 的詞彙](../../adapters-and-accelerators/accelerator-rosettanet/step-2-defining-and-publishing-the-vocabulary-for-contoso.md)