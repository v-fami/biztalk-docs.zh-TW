---
title: 建立或編輯夥伴 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- creating, trading partners
- trading partners
- modifying, trading partners
- trading partners, creating
- trading partners, modifying
- trading partners, about trading partners
ms.assetid: 63809035-65a5-472d-b2e5-359c8e9d9d8c
caps.latest.revision: 4
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b6e5f8c666de367860ad4243be444cecac6fa8bf
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37012663"
---
# <a name="creating-or-editing-a-partner"></a>建立或編輯夥伴
本主題描述如何建立或編輯交易夥伴。 交易夥伴組態描述與分類交易夥伴、設定來源不可否認性的時段、設定交易夥伴的憑證，以及提供連絡人資訊。  

 當您第一次建立夥伴時，Microsoft[!INCLUDE[BTARN_CurrentVersion_FirstRef](../../includes/btarn-currentversion-firstref-md.md)]會建立兩個傳送埠以供該夥伴，其中一個非同步和同步。 這些傳送埠分別命名為\<*夥伴名稱*\>。非同步傳送埠並\<*夥伴名稱*\>。同步傳送埠。 [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] 自動登錄並啟動這些傳送埠根據夥伴協議。 您可以在 BizTalk 管理主控台中檢視這些傳送埠。  

 下表根據索引標籤來排列，顯示交易夥伴設定。有關如何建立與編輯交易夥伴的說明，請參閱表格後的程序。  


|                            索引標籤                             |            設定            |                                                                                                                                                                                                                                                                                                                                                                                    使用方式                                                                                                                                                                                                                                                                                                                                                                                    |
|------------------------------------------------------------|-------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|                        **一般**                         |           **名稱**            |                                                                                                                                                                                                                                                                                                                                        交易夥伴的名稱。<br /><br /> 必要的欄位。<br /><br /> 最大長度： 255                                                                                                                                                                                                                                                                                                                                        |
|                        **一般**                         |            **GBI**            |                                                                                                                                                                                                                                                                                                             交易夥伴的「全球商務識別碼」。 此識別碼的長度必須為九個數字，且必須與 DUNS 編號相符。<br /><br /> 必要的欄位。                                                                                                                                                                                                                                                                                                              |
|                        **一般**                         |        **說明**        |                                                                                                                                                                                                                                                                                                                                                                 識別交易夥伴的描述。                                                                                                                                                                                                                                                                                                                                                                  |
|                        **一般**                         |        **保留至**         |                                                                                       日期[!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)]會提交訊息至 MessagesFromLOB 資料表。 [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] 將不會傳送此訊息，直到**保留至**日期。 交易夥伴必須根據接收交易夥伴何時可準備好接收訊息，決定是否同意此日期。 若交易夥伴無法處理訊息時，例如，在假日期間，則此設定可能很有用。<br /><br /> 預設值為目前日期。                                                                                       |
|                        **一般**                         |  **夥伴分類**   |            交易夥伴組織的類型。<br /><br /> 可以是**載波**（預設值），**散發者**，**終端使用者**，**政府機關使用者**， **Financier**，**製造商**，**零售商**，或**購物者**。<br /><br /> [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] 將此欄位的值放在「服務」標頭內。<br /><br /> 在協議的 [自訂屬性] 索引標籤中輸入 PPCC 自訂屬性，就可以把訊息服務標頭中的夥伴分類改成其他值，藉以覆寫這個屬性。 如需詳細資訊，請參閱 <<c0> [ 建立或編輯協議](../../adapters-and-accelerators/accelerator-rosettanet/creating-or-editing-an-agreement.md)。            |
|                        **一般**                         | **不可否認性的來源** | 天數[!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)]將不可否認性 （可法定證明對方已收到它） 的 MessageStorageIn 或 MessageStorageOut 資料庫中保留訊息的電傳格式。 [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] 每個傳入或傳出訊息上標示這個日期。<br /><br /> 預設值是 2485 天。<br /><br /> 不過，超過這個時間後，[!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] 並不會從資料庫中刪除訊息。 若要刪除這些訊息，請建立 SQL 指令碼，根據此日期/時間戳記來刪除舊訊息。 |
| **一般**<br /><br /> (**公開金鑰憑證**區域) |         **簽章**         |                                                                                                                                                     [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] 用來在內送訊息上確認交易夥伴簽章的公開金鑰憑證。 此憑證必須存放在 [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] 管理主控台中 [憑證 (本機電腦)] 節點的 [其他人] 憑證存放區。<br /><br /> 預設值是\<無\>。                                                                                                                                                     |
| **一般**<br /><br /> (**公開金鑰憑證**區域) |        **加密**         |                                                                                                                                                       [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] 用來加密傳送至交易夥伴訊息的公開金鑰加密憑證。 此憑證必須存放在 [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] 管理主控台中 [憑證 (本機電腦)] 節點的 [其他人] 憑證存放區。<br /><br /> 預設值是\<無\>。                                                                                                                                                       |
|                   **連絡人屬性**                   |       **連絡人名稱**        |                                                                                                                                                                                                                                                                                                                                                     交易夥伴連絡人的名稱。<br /><br /> 必要的欄位。                                                                                                                                                                                                                                                                                                                                                     |
|                   **連絡人屬性**                   |      **電子郵件地址**       |                                                                                                                                                                                                                                                                                                                                                交易夥伴連絡人的電子郵件地址。<br /><br /> 必要的欄位。                                                                                                                                                                                                                                                                                                                                                |
|                   **連絡人屬性**                   |     **電話號碼**      |                                                                                                                                                                                                                                                                                                                                              交易夥伴連絡人的電話號碼。<br /><br /> 必要的欄位。                                                                                                                                                                                                                                                                                                                                               |
|                   **連絡人屬性**                   |        **傳真號碼**         |                                                                                                                                                                                                                                                                                                                                                 交易夥伴連絡人的傳真號碼。<br /><br /> 必要的欄位。                                                                                                                                                                                                                                                                                                                                                  |
|                   **連絡人屬性**                   |     **供應鏈代碼**     |                                                                                                                                                                                                                                                                                                                    交易夥伴的供應鏈代碼。 例如，"Information Technology" 或 "Electronic Components"。<br /><br /> 必要的欄位。                                                                                                                                                                                                                                                                                                                     |

### <a name="to-create-a-partner"></a>建立夥伴  

1. 按一下 **開始**，指向**所有程式**，指向**Microsoft**[!INCLUDE[btaBTARNNoVersionui](../../includes/btabtarnnoversionui-md.md)]，然後按一下[!INCLUDE[btaBTARNNoVersionui](../../includes/btabtarnnoversionui-md.md)] **Management Console**.  

2. 在 BTARN 管理主控台中，展開 [[!INCLUDE[btaBTARNNoVersionui](../../includes/btabtarnnoversionui-md.md)]]。  

3. 以滑鼠右鍵按一下**合作夥伴**，指向**新增**，然後按一下**夥伴**。  

4. 在 **新交易夥伴屬性**對話方塊的 **一般**並**連絡人屬性**索引標籤上，設定的型別值。 如需有關這些設定的詳細資訊，請參閱上表。  

5. 按一下 [確定] 。  

### <a name="to-edit-a-partner"></a>編輯夥伴  

1. 按一下 **開始**，指向**所有程式**，指向**Microsoft**[!INCLUDE[btaBTARNNoVersionui](../../includes/btabtarnnoversionui-md.md)]，然後按一下[!INCLUDE[btaBTARNNoVersionui](../../includes/btabtarnnoversionui-md.md)] **Management Console**.  

2. 在 BTARN 管理主控台中，依序展開[!INCLUDE[btaBTARNNoVersionui](../../includes/btabtarnnoversionui-md.md)]，然後按一下**合作夥伴**。  

3. 以滑鼠右鍵按一下您要編輯，然後按一下 夥伴**屬性**。  

4. 在  **\<**<em>夥伴</em>**\>** 屬性對話方塊的 **一般**和**連絡人屬性**索引標籤上，視需要變更設定。 如需有關這些設定的詳細資訊，請參閱上表。  

5. 按一下 [確定] 。  

## <a name="see-also"></a>另請參閱  
 [管理設定、 憑證、 資料庫和安全性](manage-configuration-certificates-databases-security.md)   
 [管理 BTARN 設定](../../adapters-and-accelerators/accelerator-rosettanet/administering-the-btarn-configuration.md)