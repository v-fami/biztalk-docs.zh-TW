---
title: MllpSend 工具 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- MllpSend tool
- MLLP-encoded messages, receive adapters
- MLLP-encoded messages, MllpSend tool
ms.assetid: b1723d52-4909-4543-8215-4f73802b6c4f
caps.latest.revision: 6
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ed9b666b019fe7dc415f28c0dd01522b728b149c
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
ms.locfileid: "25960724"
---
# <a name="mllpsend-tool"></a>MllpSend 工具
您可以使用 MllpSend 工具來傳送資料至 MLLP 的接收位置。  
  
 安裝此工具透過[!INCLUDE[HL7_CurrentVersion_FirstRef](../../includes/hl7-currentversion-firstref-md.md)]自訂安裝程序。 如果您執行一般安裝 BTAHL7 安裝，然後您必須執行自訂安裝並測試工具安裝進行本教學課程正常運作。 在 [自訂安裝] 畫面中，選取**MLLP 測試工具**從**配接器**資料夾，然後選取**測試執行個體**從**成品**資料夾。 如需詳細資訊，請參閱[執行自訂安裝](http://msdn.microsoft.com/library/e55c86e1-af63-49ba-8510-d177e1b96692)。  
  
 BTAHL7 安裝程式會安裝在此工具*\<磁碟機\>*: \Program Files\Microsoft BizTalk\<版本\>Accelerator for HL7\SDK\MLLP 公用程式。  
  
 您使用此工具中的[端對端教學課程](../../adapters-and-accelerators/accelerator-hl7/end-to-end-tutorial1.md)、 [Interrogative 教學課程](../../adapters-and-accelerators/accelerator-hl7/interrogative-tutorial.md)、[批次的教學課程](../../adapters-and-accelerators/accelerator-hl7/batching-tutorial.md)，而[訊息擴充教學課程](../../adapters-and-accelerators/accelerator-hl7/message-enrichment-tutorial.md). 如果您已安裝[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]透過預設安裝中，且尚未安裝 MLLP 的 Testtools （包括 MllpSend 和 MllpReceive），您不能測試您的教學課程結果。  
  
## <a name="tool-usage"></a>工具使用方式  
 下列顯示您用來叫用這個命令列工具的語法：  
  
```  
mllpsend.exe [/?] [/I <IP>] [/P <PORT>] [/TWOWAY] [/REPEAT <n>] [/F <FILENAME> | "TEXT"] /SB nn /EB nn /CR nn  
```  
  
 下表說明每一部分 MllpSend 工具使用的語法。  
  
|語法|Description|  
|------------|-----------------|  
|**/?**|在命令提示字元 視窗中顯示說明。|  
|**/I \<IP\>**|表示要傳送至的位址。 預設值為 localhost。|  
|**/P\<連接埠\>**|表示將傳送至連接埠號碼。 預設值是**11000**。|  
|**/F**|傳送檔案的檔案名稱的內容。|  
|**/ 重複\<n\>**|會傳送相同訊息*n*時間。 包裝函式的字元將會套用至各個訊息。|  
|**/ TWOWAY**|寄件者會等候來自接收者的回應。 必須指定 SB 和 EB。 CR 是選擇性的。 在 檔案模式中，回應會儲存在檔案的檔案。回應。|  
|**/SB**|設定開始區塊分隔符號位元組的 ASCII 值。 預設值為 none。|  
|**/EB**|設定結束區塊分隔符號位元組的 ASCII 值。 預設值為 none。|  
|**/CR**|設定的歸位字元傳回分隔符號位元組的 ASCII 值。 預設值為 none。|  
  
## <a name="examples-of-tool-use"></a>工具使用的範例  
 下列範例會示範如何使用 MllpSend 工具。  
  
 **範例 1。** 您可以使用下列命令，將訊息傳送至單向介面卡接聽連接埠 13000"myserver"伺服器上。 包裝函式字元的 ASCII 值為 SB 11、 EB 28 和 CR 13。  
  
```  
mllpsend.exe /I myserver /P 13000 /SB 11 /EB 28 /CR 13 "A short message"  
```  
  
 **範例 2。** 您可以使用下列命令，將訊息 100 次傳送至雙向介面卡上接聽連接埠 11000 server"localhost"。 包裝函式字元的 ASCII 值為 SB 11、 EB 28 和 CR 13。  
  
```  
mllpsend.exe /SB 11 /EB 28 /CR 13 /TWOWAY /REPEAT 100 "A short message"  
```  
  
## <a name="see-also"></a>請參閱  
 [公用程式](../../adapters-and-accelerators/accelerator-hl7/utilities2.md)