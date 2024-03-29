---
title: 設定 CIDX eStandards 訊息交換 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- CIDX, configuring message exchange
ms.assetid: 90468459-cef7-436b-8c0b-3a7455a091c3
caps.latest.revision: 4
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f2aef1c49ca4bb87ef2e9388b9cdfcc86d2f35f1
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36988863"
---
# <a name="setting-up-cidx-estandards-message-exchange"></a>設定 CIDX eStandards 訊息交換
本主題描述如何設定 CIDX (化學資料交換) eStandards 訊息交換。 CIDX 要求設定下列三項屬性：  
  
- `Standard` 中的程序組態設定的屬性**CIDX**  
  
- 在程序組態設定中設定為 `True` 的 `Is Single Action` 屬性  
  
- `0A1 agreement` 在交易夥伴協議屬性**無 0A1**  
  
  CIDX 與 RosettaNet 之間差異的詳細資訊，請參閱[CIDX 支援](../../adapters-and-accelerators/accelerator-rosettanet/cidx-support.md)。  
  
### <a name="to-set-up-cidx-message-exchange"></a>設定 CIDX 訊息交換  
  
1. 按一下 **開始**，指向**所有程式**，指向**Microsoft** [!INCLUDE[btaBTARNNoVersionui](../../includes/btabtarnnoversionui-md.md)]，然後按一下[!INCLUDE[btaBTARNNoVersionui](../../includes/btabtarnnoversionui-md.md)] **Management Console**.  
  
2. 在 [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] 管理主控台中，展開 [[!INCLUDE[btaBTARNNoVersionui](../../includes/btabtarnnoversionui-md.md)]]。  
  
3. 以滑鼠右鍵按一下**程序組態設定**，指向**新增**，然後按一下**程序組態**。  
  
4. 在新的程序組態屬性 對話方塊中，在**一般**索引標籤上，如**標準**屬性中，選取**CIDX**。  
  
5. 上**活動**索引標籤上，如**單向動作**屬性中，選取**True**。  
  
6. 視需要，輸入其他程序組態設定。 如需這些設定的詳細資訊，請參閱中的資料表[如何建立或編輯流程組態](../../adapters-and-accelerators/accelerator-rosettanet/how-to-create-or-edit-a-process-configuration.md)。  
  
7. 按一下 [確定] 。  
  
8. 以滑鼠右鍵按一下**協議**，指向**新增**，然後按一下**協議**。  
  
9. 在上**一般**，**連接埠**，**通訊協定**，以及**自訂屬性**索引標籤上，輸入各種設定的值。 如需這些設定的詳細資訊，請參閱中的資料表[建立或編輯協議](../../adapters-and-accelerators/accelerator-rosettanet/creating-or-editing-an-agreement.md)。  
  
10. 在 [新協議屬性] 對話方塊中，在**一般**索引標籤上，如**0A1 協議**屬性中，選取**No 0A1**。  
  
11. 按一下 [確定] 。  
  
## <a name="see-also"></a>另請參閱  
 [如何建立或編輯流程組態](../../adapters-and-accelerators/accelerator-rosettanet/how-to-create-or-edit-a-process-configuration.md)   
 [建立或編輯協議](../../adapters-and-accelerators/accelerator-rosettanet/creating-or-editing-an-agreement.md)   
 [建立或編輯主要組織](../../adapters-and-accelerators/accelerator-rosettanet/creating-or-editing-a-home-organization.md)   
 [建立或編輯夥伴](../../adapters-and-accelerators/accelerator-rosettanet/creating-or-editing-a-partner.md)