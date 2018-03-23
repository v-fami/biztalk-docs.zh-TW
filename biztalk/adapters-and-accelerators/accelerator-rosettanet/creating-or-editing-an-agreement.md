---
title: 建立或編輯協議 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- agreements, about agreements
- agreements, modifying
- agreements, creating
- agreements
- trading partners, agreements
- creating, agreements
- modifying, agreements
- agreements, trading partners
ms.assetid: 4bbe4b57-d6ec-4448-9c80-2aecd98e0dc7
caps.latest.revision: ''
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 1ea033770504b0e0024a831e0ad8d8727603046e
ms.sourcegitcommit: 8418b1a8f38b7f56979cd6e203f0b591e2f40fe1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/23/2018
---
# <a name="creating-or-editing-an-agreement"></a>建立或編輯協議
本主題說明如何建立或編輯交易夥伴協議。 交易夥伴協議設定兩個交易夥伴之間的關係，包括其身份識別；交易夥伴介面程序 (PIP)；動作、信號與同步 URL；以及關聯的協定。  
  
 交易夥伴協議包含程序組態、主要組織、交易夥伴與協議的設定。 這些皆為協議的必要設定。 您可以根據 RosettaNet PIP 或自訂結構描述來建立程序組態，但無論如何，您必須建立組態。 您也必須定義主要組織和夥伴組織。 [!INCLUDE[btsCoName](../../includes/btsconame-md.md)][!INCLUDE[BTARN_CurrentVersion_FirstRef](../../includes/btarn-currentversion-firstref-md.md)] 不支援未知合作對象之間交換訊息。  
  
 [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] 根據所有這些設定來處理與驗證訊息。 以 CIDX 訊息為例，[!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] 將根據 RosettaNet 實作架構 (RNIF) 版本 (僅限 1.1)、0A1 協議 (僅限 No 0A1) 與 `Is Single Action` 屬性 (僅限單向動作) 進行驗證。 只有當您將 RNIF 版本設為"1.1"，為 「 No 0A1 」，將 0A1 協議，將會驗證 CIDX 訊息和`Is Single Action`屬性`True`。 [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] 也會驗證任何協議屬性與程序組態設定檔設定一致。 例如，它會驗證您是否將設定檔的 `Standard` 屬性設為 CIDX，並將協議的 0A1 協議屬性設為 No 0A1。  
  
 當程序仍在作用中時，若對協議作任何修改，就可能會發生無法預測的結果。 協議屬性變更會套用，當您按一下**套用**或**確定**接受，但您無法預測執行哪一個階段的程序。 當您更改了協議之後，目前程序或任何新程序中的任何新活動，都會使用變更過的協議屬性。 但在您變更協議的同時執行的程序，可能會對它正在處理的訊息使用先前的協議屬性。  
  
 建立協議後，您必須啟動協議，才能傳送或接收與協議關聯的訊息。 您也可以停用協議以避免傳送或接收任何與協議關聯的訊息。 您必須停用協議後才能編輯協議，並在編輯後重新啟動協議。  
  
 [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] 將此資訊儲存在 BTARNCONFIG 資料庫的 TPAConfig 資料表。  
  
 下表根據索引標籤來排列，顯示交易夥伴協議的設定。預設設定為最常用的設定值。 建立與編輯這些設定的程序，列在此表格之後。  
  
|索引標籤|設定|使用方式|  
|---------|-------------|-----------|  
|**一般**|**名稱**|協議的唯一名稱，例如，Fabrikam_To_Contoso_3A2。<br /><br /> 必要的欄位。|  
|**一般**|**程序組態**|PIP 的識別碼。<br /><br /> 此數字可用來識別此協議所關聯的程序組態。<br /><br /> 程序組態清單中的第一個值就是預設值。 下拉式清單中包含先前輸入的所有程序組態。<br /><br /> 必要的欄位。|  
|**一般**|**我的組織**|主要組織，可從下拉式清單中選取。<br /><br /> 必要的欄位。|  
|**一般**|**夥伴組織**|交易夥伴組織，可從下拉式清單中選取。<br /><br /> 必要的欄位。|  
|**一般**|**說明**|交易夥伴協議的描述。|  
|**一般**|**RNIF 版本**|[!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] 用以做為協議通訊的 RNIF 版本。<br /><br /> 可以是**V01.10.00**或**V02.00.01** （預設值）。<br /><br /> 必須是**V01.10.00**對 CIDX。|  
|**一般**|**主要角色**|主要組織的角色。<br /><br /> 可能為啟動者角色或回應者角色。|  
|**一般**|**0A1 協議**|決定發生失敗時，[!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] 是否應傳回「通知」或「失敗」訊息 (0A1 PIP)。<br /><br /> 可以是**No 0A1** （預設值） 或**0A1**。<br /><br /> 必須是**No 0A1**對 CIDX。|  
|**一般**|**使用方式**|指示協議所用的實例類型。<br /><br /> 可以是**測試**（預設值） 或**生產**。|  
|**一般**<br /><br /> (**應用程式配接器**區域)|**組件名稱**|ApplicationAdapter 的檔案名稱，您可從檔案系統中選取。<br /><br /> 預設值為空字串。|  
|**一般**<br /><br /> (**應用程式配接器區域**)|**類別名稱**|[!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] 從 ApplicationAdapter 選用的類別名稱。<br /><br /> 預設值是\<無\>。|  
|**一般**<br /><br /> (**驗證配接器區域**)|**組件名稱**|ValidationAdapter 的檔案名稱，您可從檔案系統中選取。 預設值為空字串。|  
|**一般**<br /><br /> (**驗證配接器區域**)|**類別名稱**|[!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] 從 ValidationAdapter 選用的類別名稱。<br /><br /> 預設值是\<無\>。|  
|**連接埠**|**動作 URL**|主要組織傳輸動作訊息的目標 URL。 例如，http://FabrikamServer/BTARNApp/RNIFReceive.aspx。<br /><br /> 若下列情況為真，則此為必要的欄位：<br /><br /> -**同步**程序組態設定是`False`。<br /><br /> -**單向動作**程序組態設定是`True`。<br /><br /> -**主要角色**協議設定為**啟動器**。<br /><br /> 這也是如果下列條件成立時必要的欄位 (在此情況下，**信號 URL**欄位也是必要):<br /><br /> -**同步**程序組態設定是`False`。<br /><br /> -**單向動作**程序組態設定是`False`。<br /><br /> -您必須輸入有效的 URI，在此欄位中，它的開頭是"http://domain"或"https://domain"。|  
|**連接埠**|**信號 URL**|主要組織傳輸信號訊息的目標 URL。 例如，http://FabrikamServer/BTARNApp/RNIFReceive.aspx。<br /><br /> 若下列情況為真，則這是必要欄位：<br /><br /> -**同步**程序組態設定是`False`。<br /><br /> -**單向動作**程序組態設定是`True`。<br /><br /> -**主要角色**協議設定為**回應**。<br /><br /> 這也是如果下列條件成立時必要的欄位 (在此情況下，**動作 URL**欄位也是必要):<br /><br /> -**同步**程序組態設定是`False`。<br /><br /> -**單向動作**程序組態設定是`False`。<br /><br /> 您必須在此欄位中輸入有效的 URI，它的開頭必須是 "http://domain" 或 "https://domain"。|  
|**連接埠**|**同步 URL**|主要組織經由 HTTP 配接器建立連線所用的 URL。 例如，http://FabrikamServer/BTARNApp/RNIFReceive.aspx。<br /><br /> 若下列情況為真，則這是必要欄位：<br /><br /> -**同步**程序組態設定是`True`。<br /><br /> -**主要角色**協議設定為**啟動器**。<br /><br /> 您必須在此欄位中輸入有效的 URI，它的開頭必須是 "http://domain" 或 "https://domain"。|  
|**通訊協定**|**摘要方法**|為達到不可否認性目的，用來計算內送訊息摘要的通訊協定。<br /><br /> **從開始[!INCLUDE[bts2016_md](../../includes/bts2016-md.md)]和較新版本**，SHA2 支援會自動包含。 選項包括： **MD5**， **sha-1**， **sha-256** （預設）、 **sha-384**，和**sha-512**。<br /><br />如先前[!INCLUDE[btsBizTalkServerNoVersion_md](../../includes/btsbiztalkservernoversion-md.md)]版本中，選項包括**MD5**或**sha-1** （預設值）。<br /><br /> [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)]接收管線會接收並解密訊息，即使使用來加密訊息的通訊協定和**編碼**協議的此索引標籤上的設定不相符。 因此，[!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)]接收以 RC2-40 或 3DES 加密的訊息。<br /><br /> 所有帶正負號的外寄訊息有 sha-1 的摘要。|  
|**通訊協定**|**編碼所有的部分**|決定系統是否一起編碼 Multipart 訊息的所有部分。<br /><br /> 可能為 `True` 或 `False` (預設值)。<br /><br /> 當`True`，一起使用指定的方法就會編碼 multipart 訊息的所有部分`Encoding`屬性。<br /><br /> 若為 `False`，系統將使用 `Encoding` 屬性指定的方法只對附件進行編碼 (附件一律由傳送管線以 `Encoding` 屬性所指定的方法進行編碼)。當這個屬性設定為 `False` 時，[!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] 預設會將訊息的其他部分 (在 RNIF 2.01 為四部分，在 RNIF 1.1 為三部分) 編碼成 quoted-printable 格式。|  
|**通訊協定**|**編碼方式**|用來編碼所有部分的通訊協定 (如果**都編碼所有部分**方塊`True`) 或附件 (如果**都都編碼所有部分**方塊`False`)。<br /><br /> 可以是**8 位元**， **base 64** （預設值），或**加上引號的可列印**。|  
|**通訊協定**|**加密演算法**|用來加密內送與外寄訊息的演算法。<br /><br /> **從開始[!INCLUDE[bts2016_md](../../includes/bts2016-md.md)]和較新版本**，AES 支援會自動包含。 選項包括**RC2-40**， **3DES**， **AES128** （預設）、 **AES192**，和**AES256**。 <br /><br />如先前[!INCLUDE[btsBizTalkServerNoVersion_md](../../includes/btsbiztalkservernoversion-md.md)]版本中，選項包括**RC2-40** （預設值） 或**3DES**。<br /><br /> 加密演算法才會生效，如果您已將`Is Persistent Confidentiality Required`屬性設為**裝載**或**Payload Container**在對應的處理序組態。|  
|**通訊協定**|**加密方向**|決定系統將加密內送訊息或外寄訊息，或是兩者皆加密。<br /><br /> 可以是**輸入**，**輸出**，或**輸入/輸出**（預設值）。<br /><br /> 加密方向設定才會生效，如果您已將`Is Persistent Confidentiality Required`屬性設為**裝載**或**Payload Container**在對應的處理序組態。|  
|**自訂屬性**|**名稱**|自訂屬性的名稱。<br /><br /> 您可以分別為每個協議設定自訂屬性名稱。 若您建立新的自訂私用程序，可使用這些自訂屬性來處理不同的協議。<br /><br /> 您可以使用 [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] SDK 中的 `RuntimeConfig.GetTPACustomConfigValue` 方法，從 [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] 組態中擷取自訂屬性。<br /><br /> `Name` 屬性必須是唯一的，且不得為空白。<br /><br /> 您可以輸入以下的自訂值：<br /><br /> - **AAR**。 這是「需要接受通知」(Acceptance Acknowledgment Required) 自訂屬性， 僅適用於 RNIF 1.1。 將此設**false** （此為不區分大小寫） 要求只接收通知，不接受通知。 如果**AAR**以外設為  **false**、 然後回應者公開程序必須傳送接受通知，也無法啟動者公開程序會接受通知。 若 AAR 設定為 false，公開處理程序在接收通知之後就算完成。<br /><br /> - **HPCC**. 代表 Home Partner Classification Code (主要夥伴分類代碼)， 僅適用於 RNIF 1.1。 讓您可以將外寄訊息服務標頭中的主要夥伴 GlobalPartnerClassificationCode 項目設定為「值」欄位中的項目。 這個值覆寫了「主要組織」組態中的「主要」組織分類屬性。 當主要組織的分類不只一種時，可以使用這個自訂屬性。<br /><br /> - **PPCC**. 代表 Partner Profile Classification Code (夥伴設定檔分類代碼)， 僅適用於 RNIF 1.1。 讓您可以將外寄訊息服務標頭中的夥伴 GlobalPartnerClassificationCode 項目設定為「值」欄位中的項目。 這個值覆寫了「夥伴」組態中的「夥伴」分類屬性。 當夥伴的分類不只一種時，可以使用這個自訂屬性。|  
|**自訂屬性**|**值**|自訂屬性的值。|  
  
### <a name="to-create-a-trading-partner-agreement"></a>建立交易夥伴協議  
  
1.  按一下**啟動**，指向 **所有程式**，指向  **Microsoft** [!INCLUDE[btaBTARNNoVersionui](../../includes/btabtarnnoversionui-md.md)]，然後按一下[!INCLUDE[btaBTARNNoVersionui](../../includes/btabtarnnoversionui-md.md)]**管理主控台**.  
  
2.  在 BTARN 管理主控台中，展開 [[!INCLUDE[btaBTARNNoVersionui](../../includes/btabtarnnoversionui-md.md)]]。  
  
3.  以滑鼠右鍵按一下**協議**，指向 **新增**，然後按一下 **協議**。  
  
4.  在 [新協議屬性] 對話方塊上**一般**，**連接埠**，**通訊協定**，和**Custom Properties**索引標籤上，輸入值設定。 如需有關這些設定的詳細資訊，請參閱上表。  
  
5.  按一下 **[確定]**。  
  
    > [!NOTE]
    >  在您啟動協議之前，BTARN 都不會接收與此協議相關的訊息。  
  
6.  以滑鼠右鍵按一下右窗格中的協議的名稱，然後按一下  **Activate**。  
  
> [!NOTE]
>  如果您已經啟動協議，您可以以滑鼠右鍵按一下右窗格中的協議的名稱，然後按一下**停用**來避免傳送或接收協議相關聯的任何訊息。  
  
### <a name="to-edit-a-trading-partner-agreement"></a>編輯交易夥伴協議  
  
1.  按一下**啟動**，指向 **所有程式**，指向  **Microsoft** [!INCLUDE[btaBTARNNoVersionui](../../includes/btabtarnnoversionui-md.md)]，然後按一下[!INCLUDE[btaBTARNNoVersionui](../../includes/btabtarnnoversionui-md.md)]**管理主控台**.  
  
2.  在 BTARN 管理主控台中，依序展開[!INCLUDE[btaBTARNNoVersionui](../../includes/btabtarnnoversionui-md.md)]，然後按一下 **協議**節點。  
  
3.  以滑鼠右鍵按一下您想要編輯，然後按一下 協議**屬性**。  
  
4.  在**\<***協議名稱***\>**屬性對話方塊中，於**一般**和**連絡人屬性**索引標籤上，視需要變更設定。 如需有關這些設定的詳細資訊，請參閱上表。  
  
5.  按一下 **[確定]**。  
  
## <a name="see-also"></a>另請參閱  
 [管理設定、 憑證、 資料庫和安全性](manage-configuration-certificates-databases-security.md)   
 [管理 BTARN 設定](../../adapters-and-accelerators/accelerator-rosettanet/administering-the-btarn-configuration.md)