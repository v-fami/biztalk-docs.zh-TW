---
title: "建立或編輯主要組織 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- home organizations, about home organizations
- home organizations, modifying
- creating, home organizations
- modifying, home organizations
- home organizations
- home organizations, creating
ms.assetid: b54afb84-2f16-4516-8701-b03301476362
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 4bc8a298686772d354c934d76fbcb7dbbb8146f8
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="creating-or-editing-a-home-organization"></a>建立或編輯主要組織
本主題描述如何建立或編輯主要組織。 主要組織組態描述與分類主要組織、設定來源不可否認性的時段，以及提供連絡人資訊。  
  
 主要組織組態與交易夥伴組態相同，皆不包含簽章與解密憑證。 您設定 BizTalk 群組中的簽章憑證[!INCLUDE[btsCoName](../../includes/btsconame-md.md)][!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台。 請在 [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台中為 BizTalk 主控件 (BizTalkServerApplication 與 BizTalkIsolatedHost) 設定解密憑證。  
  
 您可以在單一公司或部署中，建立兩個主要組織。 此做法的範例之一，便是要建立訊息處理的優先順序，使不同組織的相關訊息，有不同的優先處理順序。 當您建立多個主要組織時，必須為每個主要組織提供不同的 DUNS 編號，以獨特方式辨識主要組織。 DUNS 編號定義了 RosettaNet 連線。  
  
 下表根據索引標籤來排列，顯示主要組織的設定。有關如何建立與編輯主要組織的說明，請參閱表格後的程序。  
  
|索引標籤|設定|使用方式|  
|---------|-------------|-----------|  
|**一般**|**名稱**|主要組織的名稱。<br /><br /> 必要的欄位。<br /><br /> 最大長度： 255|  
|**一般**|**GBI**|主要組織的「全球商務識別碼」。 此識別碼的長度必須為九個數字，且必須與 DUNS 編號相符。<br /><br /> 必要的欄位。|  
|**一般**|**說明**|協助識別主要組織的描述。|  
|**一般**|**主要組織分類**|組織的特性。<br /><br /> 可以是**終端使用者**，**終端使用者政府**， **financier**，**製造商**，**零售商**， **購物者**，**運費轉寄站**，或**Marketplace**。<br /><br /> 在協議的 [自訂屬性] 索引標籤中輸入 HPCC 自訂屬性，就可以把訊息服務標頭中的主要組織分類改成其他值，藉以覆寫這個屬性。 如需詳細資訊，請參閱[建立或編輯協議](../../adapters-and-accelerators/accelerator-rosettanet/creating-or-editing-an-agreement.md)。|  
|**連絡人屬性**|**連絡人名稱**|主要組織連絡人的名稱。<br /><br /> 必要的欄位。|  
|**連絡人屬性**|**電子郵件地址**|主要組織連絡人的電子郵件地址。<br /><br /> 必要的欄位。|  
|**連絡人屬性**|**電話號碼**|主要組織連絡人的電話號碼。<br /><br /> 必要的欄位。|  
|**連絡人屬性**|**傳真號碼**|主要組織連絡人的傳真號碼。<br /><br /> 必要的欄位。|  
|**連絡人屬性**|**供應鏈代碼**|主要組織的供應鏈代碼。<br /><br /> 必要的欄位。|  
  
### <a name="to-create-a-home-organization-definition"></a>建立主要組織定義  
  
1.  按一下**啟動**，指向 **所有程式**，指向  **Microsoft** [!INCLUDE[btaBTARNNoVersionui](../../includes/btabtarnnoversionui-md.md)]，然後按一下[!INCLUDE[btaBTARNNoVersionui](../../includes/btabtarnnoversionui-md.md)]**管理主控台**.  
  
2.  在 BTARN 管理主控台中，展開 [[!INCLUDE[btaBTARNNoVersionui](../../includes/btabtarnnoversionui-md.md)]]。  
  
3.  以滑鼠右鍵按一下**主要組織**，指向 **新增**，然後按一下 **主要組織**。  
  
4.  在 [新主要組織屬性] 對話方塊上**一般**和**連絡人屬性**索引標籤上，輸入設定值。 如需有關這些設定的詳細資訊，請參閱上表。  
  
5.  按一下 **[確定]**。  
  
### <a name="to-edit-a-home-organization"></a>編輯主要組織  
  
1.  按一下**啟動**，指向 **所有程式**，指向  **Microsoft** [!INCLUDE[btaBTARNNoVersionui](../../includes/btabtarnnoversionui-md.md)]，然後按一下[!INCLUDE[btaBTARNNoVersionui](../../includes/btabtarnnoversionui-md.md)]**管理主控台**.  
  
2.  在 BTARN 管理主控台中，展開 [[!INCLUDE[btaBTARNNoVersionui](../../includes/btabtarnnoversionui-md.md)]]。  
  
3.  按一下**Home 組織**。  
  
4.  以滑鼠右鍵按一下您想要編輯，然後按一下 主要組織**屬性**。  
  
5.  在 *\<home 組織 >*屬性對話方塊中，於**一般**和**連絡人屬性**索引標籤上，視需要變更設定。 如需有關這些設定的詳細資訊，請參閱上表。  
  
6.  按一下 **[確定]**。  
  
## <a name="see-also"></a>另請參閱  
 [管理設定、 憑證、 資料庫和安全性](manage-configuration-certificates-databases-security.md)   
 [管理 BTARN 組態](../../adapters-and-accelerators/accelerator-rosettanet/administering-the-btarn-configuration.md)