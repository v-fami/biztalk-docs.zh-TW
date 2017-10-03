---
title: "如何建立或編輯程序組態 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- process configuration, modifying
- process configuration, creating
- authorization properties
- non-repudiation, properties
- creating, process configuration
- modifying, process configuration
ms.assetid: ef6160f1-f2f0-42ff-a516-7818c9d79d26
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e4c9c9be5e9f3361683e495febbd98a05156399d
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-create-or-edit-a-process-configuration"></a>如何建立或編輯程序組態
本主題描述如何建立或編輯程序組態。  
  
 下表根據索引標籤來排列，顯示程序組態的設定。表格後面列出用來建立與編輯程序組態的步驟。  
  
 授權與不可否認性屬性彼此相依。 如需如何設定這些屬性的詳細資訊，請參閱[授權與不可否認性屬性](../../adapters-and-accelerators/accelerator-rosettanet/authorization-and-non-repudiation-properties.md)。  
  
|索引標籤|設定|使用方式|  
|---------|-------------|-----------|  
|**一般**|**顯示程式碼**|交易夥伴介面程序 (PIP) 顯示代碼。 此代碼必須符合 RosettaNet PIP 指定，或自訂結構描述的名稱。 建議您使用標準命名慣例，例如在名稱中包含程序代碼與版本，如 STD_3A2_R02.00.00A。 如此可讓您更容易維護同一 PIP 的不同版本。<br /><br /> 必要的欄位。|  
|**一般**|**處理程序程式碼**|三個位數的 PIP 代碼。 例如 "3A2"。<br /><br /> 必要的欄位。|  
|**一般**|**版本**|PIP 的版本。 例如，"V02.02" 或 "R02.00.00A"。<br /><br /> 必要的欄位。|  
|**一般**|**處理序名稱**|PIP 的名稱。 例如，價格與可用性要求動作。<br /><br /> 必要的欄位。|  
|**一般**|**說明**|符合 PIP 的訊息描述。|  
|**一般**|**Standard**|標準的類型。<br /><br /> 可能值：RosettaNet (預設值) 或 CIDX|  
|**一般**<br /><br /> (非 RosettaNet 內容區域)|**訊息標準**|針對非 RosettaNet 內容，非 RosettaNet 標準的名稱。 若您不使用 RosettaNet PIP，但已定義自訂結構描述，請使用此設定。 此設定只能用於 RNIF 2.0，不能用於 RNIF 1.1 或 CIDX。|  
|**一般**<br /><br /> (非 RosettaNet 內容區域)|**標準版本**|針對非 RosettaNet 內容，非 RosettaNet 標準的版本。 若您不使用 RosettaNet PIP，但已定義自訂結構描述，請使用此設定。 此設定只能用於 RNIF 2.0，不能用於 RNIF 1.1 或 CIDX。|  
|**一般**<br /><br /> (非 RosettaNet 內容區域)|**承載繫結識別碼**|針對非 RosettaNet 區域，承載內容的識別碼。 若您不使用 RosettaNet PIP，但已定義自訂結構描述，請使用此設定。 實作自訂 PIP 的合作對象應該定義此值。 此設定只能用於 RNIF 2.0，不能用於 RNIF 1.1 或 CIDX。|  
|**活動**<br /><br /> ([接收通知] 區域)|**不可否認性所需**|決定接收合作對象是否應對信號訊息加上簽章 (將訊息簽章放在通知訊息內)，並以原始格式將訊息儲存在 [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)]Archive 資料庫的 MessageStorageIn 或 MessageStorageOut 資料表中，以供不可否認性目的之用。 接收合作對象必須將信號存放在指定的期間**不可否認性的原點**夥伴組態中的屬性。<br /><br /> 可能的值： `True` （預設值） 或`False`<br /><br /> 若為 `False`，將不會存放信號訊息供不可否認性目的之用。 信號訊息可以被簽署或不被簽署。<br /><br /> 若為 `True`，將使用原始格式，在 MessageStorageIn 資料表中存放輸入信號訊息。 輸出信號訊息將以其原始格式，存放在 MessageStorageOut 資料表中。 信號訊息必須經過簽署。<br /><br /> 如需詳細資訊，請參閱[授權與不可否認性屬性](../../adapters-and-accelerators/accelerator-rosettanet/authorization-and-non-repudiation-properties.md)。|  
|**活動**<br /><br /> ([接收通知] 區域)|**通知時間 （秒）**|以秒為單位的時間。啟動者必須在這段時間內接收通知。 如果起始端資料庫沒有收到它此時，起始端時重試的重試次數已超過**重試**計數 (在**行為**此索引標籤的區段)。<br /><br /> [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)]量值**通知時間**值的時間啟動者成功送出動作訊息。 設定值會包含在傳遞標頭中。 值不可小於零或大於**執行時間**相同頁面設定的值。<br /><br /> 您可以針對 RNIF 1.1 與 2.01 處理中傳回的信號訊息 (應用程式通知) 使用此設定。 也可以針對 RNIF 1.1 處理中傳回的接受通知使用此設定。<br /><br /> 預設值為 7200 秒 (兩小時)。|  
|**活動**<br /><br /> ([行為] 區域)|**需要授權嗎**|判斷是否有任何內送動作或信號訊息必須經過簽署。 [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)]若個人/角色未經授權執行活動不接受商務文件。<br /><br /> 可能的值： `True` （預設值） 或`False`<br /><br /> 若為 `False`，將不會簽署輸出動作與信號訊息。 輸入動作與信號訊息可能會經過簽署。 若未經簽署，系統將會使用傳遞標頭授權交易夥伴。<br /><br /> 若為 `True`，內送訊息必須經過簽署。 外寄訊息可能經過簽署。 只有當簽署外寄訊息**來源與內容的不可否認**設`True`。<br /><br /> 如需詳細資訊，請參閱[授權與不可否認性屬性](../../adapters-and-accelerators/accelerator-rosettanet/authorization-and-non-repudiation-properties.md)。|  
|**活動**<br /><br /> ([行為] 區域)|**是需要持續的機密性**|決定是否需要加密。<br /><br /> 可能的值：**無**（預設值） 表示不加密的必要。 **裝載**指出是否需要加密的服務內容和附件。 **內容容器**表示加密服務內容、 附件和服務標頭是必要項。<br /><br /> 在 RNIF 2.0 中，絕不會加密前序與傳遞標頭。 在 RNIF 1.1 中，不會加密訊息部分。 上述部分只會經過簽署。|  
|**活動**<br /><br /> ([行為] 區域)|**需要安全性傳輸**|決定是否需要 HTTPS 傳輸。<br /><br /> 可能的值： `True` （預設值） 或`False`|  
|**活動**<br /><br /> ([行為] 區域)|**單向動作**|決定訊息為單向動作或雙向動作。<br /><br /> 可能的值： `True` （預設值） 或`False`<br /><br /> 單向動作訊息為 [資訊散發] 或 [通知]。 雙向動作訊息為 [商務交易]、[要求確認]、[要求/回應] 或 [查詢/回應]。<br /><br /> 若標準為 CIDX，**單向動作**必須**True**。|  
|**活動**<br /><br /> ([行為] 區域)|**是同步的**|決定交易夥伴以同步或非同步的方式來交換動作訊息。<br /><br /> 可能的值：`True`或`False`（預設值）<br /><br /> 未用於 RNIF 1.1。|  
|**活動**<br /><br /> ([行為] 區域)|**不可否認性的來源與內容**|決定接收合作對象是否應對動作訊息簽署，並以原始格式將訊息存放在 BTARNArchive 資料庫中的 MessageStorageIn 或 MessageStorageOut 資料表，以供不可否認性目的之用。 接收合作對象必須存放動作訊息中指定的期間**不可否認性的原點**不可否認性目的的夥伴組態中的屬性。 必要時，就必須簽署動作訊息。<br /><br /> 可能的值： `True` （預設值） 或`False`<br /><br /> 若為 `False`，將不會存放動作訊息供不可否認性目的之用。 動作訊息可被簽署或不被簽署。<br /><br /> 若為 `True`，將使用原始格式，在 MessageStorageIn 資料表中存放輸入動作訊息。 輸出動作訊息將以其原始格式，存放在 MessageStorageOut 資料表中。 動作訊息必須經過簽署。<br /><br /> 如需詳細資訊，請參閱[授權與不可否認性屬性](../../adapters-and-accelerators/accelerator-rosettanet/authorization-and-non-repudiation-properties.md)。|  
|**活動**<br /><br /> ([行為] 區域)|**重試計數**|若傳輸或處理失敗時，程序應重試的次數。 若重試計數為 3，則程序將嘗試執行活動四次。<br /><br /> 預設值是 3。<br /><br /> 若為同步通訊，則 [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] 不會使用此欄位，因為重試不適用於同步交易。|  
|**活動**<br /><br /> ([行為] 區域)|**若要執行的時間**|程序必須完成活動的時段 (以秒為單位)。 時段是由啟動者傳送首份文件開始計算。 啟動者 (非回應者) 必須確認在此時段內完成活動。 此設定值位於傳遞標頭中。<br /><br /> 預設值為 86400 秒 （24 小時）。<br /><br /> **執行時間**值必須大於**通知時間**中所設定的值**接收通知**相同的頁面區段。|  
|**活動**<br /><br /> ([一般] 區域)|**型別**|決定活動的類型。<br /><br /> 可能的值：**商務交易**，**資訊散發**（預設）、**通知**，**查詢/回應**， **要求/確認**，或**要求/回應**|  
|**起始端**<br /><br /> ([商務文件] 區域)|**說明**|啟動者動作商務文件的描述。|  
|**起始端**<br /><br /> ([商務文件] 區域)|**名稱**|啟動者動作商務文件的名稱。 例如，價格與可用性要求。|  
|**起始端**<br /><br /> ([商務文件] 區域)|**版本**|商務文件的版本。 例如，"V02_02_00" 或 "R02.00.00A"。<br /><br /> 您可以在 RosettaNet XML Message Guidelines .htm 檔案的開頭處找到此版本編號。當您從 RosettaNet 組織下載 PIP 規格 .doc 檔案與 PIP DTD 時，會一併下載此 .htm 檔案。|  
|**起始端**<br /><br /> ([一般] 區域)|**動作**|啟動者動作的描述。 例如「同步測試查詢動作」。|  
|**起始端**<br /><br /> ([一般] 區域)|**角色**|啟動者的角色。 例如「買方」或「付費者」。<br /><br /> 預設值為「啟動者」。|  
|**起始端**<br /><br /> ([一般] 區域)|**角色描述**|啟動者角色的描述。 例如「核發付款的合作對象」。|  
|**起始端**<br /><br /> ([一般] 區域)|**角色類型**|啟動者角色的類型。<br /><br /> 可能的值：**組織**，**員工**，或**功能**（預設值）|  
|**起始端**<br /><br /> ([一般] 區域)|**服務**|啟動者服務。 例如「買方服務」或「付費者服務」。|  
|**起始端**<br /><br /> ([一般] 區域)|**服務分類**|啟動者服務的類型。 例如「商務服務」。|  
|**回應者**<br /><br /> ([商務文件] 區域)|**說明**|回應者動作商務文件的描述。 例如「正式確認訂單中項目的狀態」。|  
|**回應者**<br /><br /> ([商務文件] 區域)|**名稱**|回應者動作商務文件的名稱。 例如「訂單確認」。|  
|**回應者**<br /><br /> ([商務文件] 區域)|**版本**|商務文件的版本。 例如，"V02.02.00" 或 "R02.00.00A"。 您可以在 RosettaNet XML Message Guidelines .htm 檔案的開頭處找到此版本編號。當您從 RosettaNet 組織下載 PIP 規格 .doc 檔案與 PIP DTD 時，會一併下載此 .htm 檔案。|  
|**回應者**<br /><br /> ([一般] 區域)|**動作**|回應者動作的描述。 例如「訂單確認動作」。|  
|**回應者**<br /><br /> ([一般] 區域)|**角色**|回應者的角色。 例如「賣方」。<br /><br /> 預設值為「回應者」。|  
|**回應者**<br /><br /> ([一般] 區域)|**角色描述**|回應者角色的描述。 例如「接收付款的合作對象」。|  
|**回應者**<br /><br /> ([一般] 區域)|**角色類型**|回應者角色的類型。<br /><br /> 可能的值：**組織**（預設）、**員工**，或**功能**|  
|**回應者**<br /><br /> ([一般] 區域)|**服務**|回應者服務。 例如「賣方服務」。|  
|**回應者**<br /><br /> ([一般] 區域)|**服務分類**|回應者服務的類型。 例如「商務服務」。|  
  
### <a name="to-implement-a-new-process-configuration"></a>實作新程序組態  
  
1.  按一下**啟動**，指向 **所有程式**，指向  **Microsoft** [!INCLUDE[btaBTARNNoVersionui](../../includes/btabtarnnoversionui-md.md)]，然後按一下[!INCLUDE[btaBTARNNoVersionui](../../includes/btabtarnnoversionui-md.md)]**管理主控台**.  
  
2.  在 BTARN 管理主控台中，展開 [[!INCLUDE[btaBTARNNoVersionui](../../includes/btabtarnnoversionui-md.md)]]。  
  
3.  以滑鼠右鍵按一下**程序組態設定**，指向 **新增**，然後按一下 **程序組態**。  
  
4.  在 新程序組態屬性 對話方塊上**一般**，**活動**，**啟動器**，和**回應**索引標籤中，輸入在上述所列的設定值表格，然後按一下 **確定**。  
  
### <a name="to-edit-a-process-configuration"></a>編輯程序組態  
  
1.  按一下**啟動**，指向 **所有程式**，指向  **Microsoft** [!INCLUDE[btaBTARNNoVersionui](../../includes/btabtarnnoversionui-md.md)]，然後按一下[!INCLUDE[btaBTARNNoVersionui](../../includes/btabtarnnoversionui-md.md)]**管理主控台**.  
  
2.  在 BTARN 管理主控台中，展開 [[!INCLUDE[btaBTARNNoVersionui](../../includes/btabtarnnoversionui-md.md)]]。  
  
3.  按一下**程序組態設定**。  
  
4.  以滑鼠右鍵按一下您想要編輯，然後按一下 程序組態**屬性**。  
  
5.  在*\<程序組態 >*屬性對話方塊中，於**一般**和**連絡人屬性**索引標籤上，變更所需的設定。 如需有關這些設定的詳細資訊，請參閱上表。  
  
6.  按一下 **[確定]**。  
  
## <a name="see-also"></a>另請參閱  
 [使用 PIP 規格建立程序組態](../../adapters-and-accelerators/accelerator-rosettanet/using-the-pip-specification-to-create-a-process-configuration.md)   
 [授權與不可否認性屬性](../../adapters-and-accelerators/accelerator-rosettanet/authorization-and-non-repudiation-properties.md)   
 [設定 CIDX eStandards 訊息交換](../../adapters-and-accelerators/accelerator-rosettanet/setting-up-cidx-estandards-message-exchange.md)   
 [管理 BTARN 組態](../../adapters-and-accelerators/accelerator-rosettanet/administering-the-btarn-configuration.md)