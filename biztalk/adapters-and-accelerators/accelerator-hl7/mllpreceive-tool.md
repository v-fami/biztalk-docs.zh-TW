---
title: "MllpReceive 工具 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- MLLP-encoded messages, send adapters
- MllpReceive tool
- MLLP-encoded messages, MllpReceive tool
ms.assetid: 7069444b-1412-40bf-b567-fa86f76cd007
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 0c23aac352b47a328cfc8f412bb3beca50a61e1c
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="mllpreceive-tool"></a>MllpReceive 工具
您可以使用 MllpReceive 工具從 MLLP 傳送連接埠接收資料。  
  
 安裝此工具透過[!INCLUDE[HL7_CurrentVersion_FirstRef](../../includes/hl7-currentversion-firstref-md.md)]自訂安裝程序。 如果您執行一般安裝 BTAHL7 安裝，然後您必須執行自訂安裝並測試工具安裝進行本教學課程正常運作。 在 [自訂安裝] 畫面中，選取**MLLP 測試工具**從**配接器**資料夾，然後選取**測試執行個體**從**成品**資料夾。 如需詳細資訊，請參閱[執行自訂安裝](http://msdn.microsoft.com/library/e55c86e1-af63-49ba-8510-d177e1b96692)。  
  
 BTAHL7 安裝程式會安裝在此工具*\<磁碟機 >*: \Program Files\Microsoft BizTalk\<版本 > Accelerator for HL7\SDK\MLLP 公用程式。  
  
 您使用此工具中的[端對端教學課程](../../adapters-and-accelerators/accelerator-hl7/end-to-end-tutorial1.md)、 [Interrogative 教學課程](../../adapters-and-accelerators/accelerator-hl7/interrogative-tutorial.md)、[批次的教學課程](../../adapters-and-accelerators/accelerator-hl7/batching-tutorial.md)，而[訊息擴充教學課程](../../adapters-and-accelerators/accelerator-hl7/message-enrichment-tutorial.md). 如果您已安裝[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]透過預設安裝中，且尚未安裝 MLLPTest 的工具 （包括 MllpReceive 和 MllpSend），您不能測試您的教學課程結果。  
  
## <a name="tool-usage"></a>工具使用方式  
 下列顯示您用來叫用這個命令列工具的語法：  
  
```  
mllpreceive.exe [/?] [/I <IP>] [/P <PORT>] [/SPLIT] [/D <DIRECTORY>] [/STATICACK "ACKTEXT" | /HL7ACK <FILENAME>] /SB nn /EB nn /CR nn  
```  
  
 下表說明每一部分 MllpReceive 工具使用的語法。  
  
|語法|意義|  
|------------|-------------|  
|/?|顯示此說明。|  
|/I \<IP >|表示要接聽的位址。 預設為所有可用的 Ip。|  
|/P\<連接埠 >|表示要聆聽的連接埠號碼。 預設值是 12000。|  
|/D\<目錄 >|將所有收到的訊息儲存在目錄中\<目錄 >。 如果您未指定\<目錄 >，預設目錄是 %TEMP%。|  
|/ 分割|將已接收的資料分割成個別的分隔符號為基礎的訊息。 需要 SB 和 EB。 CR 是選擇性的。|  
|/ STATICACK|靜態通知傳回給寄件者。 將會強制執行分隔模式。|  
|/ HL7ACK|HL7 通知傳回給寄件者。 檔名表示包含 HL7 通知的檔案名稱 將會強制執行分隔模式。|  
|/SB|設定開始區塊分隔符號位元組的 ASCII 值。 預設值為 none。|  
|/EB|設定結束區塊分隔符號位元組的 ASCII 值。 預設值為 none。|  
|/CR|設定傳回分隔符號位元組的歸位字元的 ASCII 值。 預設值為 none。|  
  
## <a name="example-of-tool-use"></a>工具使用的範例  
 您可以為接聽通訊埠 10000 上 localhost，請使用下列命令，並儲存到不同的檔案在 C:\TEMP 的訊息：  
  
```  
mllpreceive.exe /P 10000 /SPLIT /SB 11 /EB 28 /CR 13 /D C:\TEMP  
```  
  
## <a name="see-also"></a>另請參閱  
 [公用程式](../../adapters-and-accelerators/accelerator-hl7/utilities2.md)