---
title: LOBApplication |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- trading partners, submitting actions
- LOBs, submitting actions
- LOBApplication utility
- trading partners, response messages
- LOBs, LOBApplication utility
- LOBs, response messages
ms.assetid: ad5986af-4175-49cd-806b-04e1fde63f55
caps.latest.revision: 7
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: dc9859e210036806cebcd76f63235d47ca972976
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36978575"
---
# <a name="lobapplication"></a>LOBApplication
您可使用 LOBApplication 公用程式將動作或回應訊息提交給交易夥伴，模擬實際的商務營運系統 (LOB) 桌面程式。  
  
 Microsoft®[!INCLUDE[BTARN_CurrentVersion_FirstRef](../../includes/btarn-currentversion-firstref-md.md)]中提供範例訊息\<*磁碟機*\>\Program 檔案 (x86) \Microsoft BizTalk\<版本\>Accelerator for RosettaNet\SDK\LOBApplication\SampleInstances 資料夾中。  
  
## <a name="location-in-sdk"></a>SDK 中的位置  
 \<*磁碟機*\>\Program 檔案 (x86) \Microsoft BizTalk\<版本\>Accelerator for RosettaNet\SDK\LOBApplication  
  
## <a name="running-lobapplication"></a>執行 LOBApplication  
  
#### <a name="to-run-lobapplication"></a>若要執行 LOBApplication  
  
1.  在 Windows 檔案總管中，移至\<*磁碟機*\>\Program 檔案 (x86) \Microsoft BizTalk\<版本\>Accelerator for RosettaNet\SDK\\。  
  
2.  按兩下**LOBApplication.exe**，然後按 ENTER 鍵。  
  
     接下來的頁面會提示您輸入執行公用程式所需的資訊。  
  
## <a name="syntax-for-lobapplication"></a>LOBApplication 的語法  
 使用**LOB Application Proxy**頁面，即可指定主要和夥伴名稱 」、 「 交易夥伴介面程序 (PIP) 屬性和 「 LOBApplication 公用程式所傳送之訊息的訊息屬性。  
  
 下表描述如何使用每個欄位上**LOB Application Proxy**頁面。  
  
|使用|以進行此動作|  
|--------------|----------------|  
|**主要設定檔名稱**|輸入主要組織 (來源合作對象) 的名稱。|  
|**交易夥伴名稱**|輸入交易夥伴 (目的合作對象) 的名稱。|  
|**PIP 名稱**|輸入 PIP，比方說，類型的顯示代碼**3A2**。 此值區分大小寫。|  
|**PIP 版本**|輸入 PIP 的版本，例如，型別**V02.00**。 此值區分大小寫。|  
|**PIP 執行個體識別碼**（選擇性）|輸入的英數字元的執行個體識別碼的 PIP，例如，輸入**STD_3A2_V02.02**。 請避免使用特殊字元。 每個夥伴和 PIP 代碼的識別碼都應該是唯一的。 對於標示為動作訊息的訊息，如果執行個體識別碼是空的，LOBApplication 公用程式就會使用產生的 HUID 值做為 PIP 執行個體識別碼。 **注意︰** 當您選取**回應**中**訊息類別**，您必須在此欄位中輸入 PIP 執行個體識別碼。|  
|**檔案名稱**|按一下省略按鈕 (...)，移至包含 PIP 執行個體檔案的資料夾，然後按一下該 PIP 執行個體檔案。|  
|**訊息類別**|選取訊息類型 (**動作**或是**回應**)。|  
|**附加檔案**|按一下 **新增**，移至包含附件檔案的資料夾，然後按一下**開啟**。|  
|**提交訊息**|按一下以傳送訊息。|  
|**狀態**|讀取此欄位中動作的狀態。|  
  
## <a name="remarks"></a>備註  
 LOBApplication 公用程式會使用指定的屬性建立訊息，並將它傳送給交易夥伴。 此公用程式會將訊息中的服務內容資料，寫入至 BTARNDATA 資料庫的 MessageFromLOB 資料表中， 並模擬傳送動作訊息。  
  
 SampleInstances 資料夾 (位於 [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] SDK 的 LOBApplication 資料夾底下) 中的範例訊息會事先設定，以採用下列全球商務識別碼 (GBI)：123456789 代表主要組織，987654321 代表交易夥伴組織。 您必須在文字編輯器中變更範例訊息，才可使用其他 GBI。  
  
 您可使用 LOBApplication 公用程式以模擬商務營運系統桌面程式提交訊息。 您可以使用 LOBWebApplication 公用程式，模擬商務營運系統 Web 應用程式提交訊息。  
  
## <a name="see-also"></a>另請參閱  
 [公用程式](../../adapters-and-accelerators/accelerator-rosettanet/utilities1.md)   
 [LOBWebApplication](../../adapters-and-accelerators/accelerator-rosettanet/lobwebapplication.md)
