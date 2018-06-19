---
title: FileTransport 範例 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a32c8cbf-0c17-4237-b2a3-9d21faa13496
caps.latest.revision: 11
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 38c08be5cd58ed6c80af351715ff6257f533c6af
ms.sourcegitcommit: 3fc338e52d5dbca2c3ea1685a2faafc7582fe23a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/01/2017
ms.locfileid: "26004999"
---
# <a name="filetransport-sample"></a>FileTransport 範例
FileTransport 範例會示範如何設定 [!INCLUDE[btsCoName](../../includes/btsconame-md.md)]® [!INCLUDE[BTARN_CurrentVersion_FirstRef](../../includes/btarn-currentversion-firstref-md.md)] 使用檔案連接埠，而不是 SQL 連接埠。 FileTransport 範例使用「檔案傳輸通訊協定」 (FTP) 取代 HTTP 來傳送和接收訊息。  
  
> [!NOTE]
>  本文件假設您安裝 [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] 只做為內部測試或示範之用。 它並未規定任何最基本的安全性帳戶或設定。 在本主題的所有程序中，您必須使用具有本機系統管理員權限的帳戶。  
  
> [!NOTE]
>  本範例不支援訊息附件。  
  
## <a name="filetransport-binding-files"></a>FileTransport 繫結檔案  
 FileTransport 範例包含兩個繫結檔案。 您可使用這兩個繫結檔案的其中一個設定「檔案」連接埠來使用 BTARN 協調流程。 這些繫結檔案位於*\<磁碟機\>*: \Program Files\Microsoft BizTalk\<版本\>Accelerator for RosettaNet \SDK\FileTransport。 請在 [記事本] 等編輯器中開啟每個繫結檔案，以查看協調流程、傳送埠、接收埠和接收位置的設定，如下所列。  
  
-   PrivateInitiatorusingFileDrops.xml  
  
    -   協調流程：Microsoft.Solutions.BTARN.PrivateInitiator.PrivateInitiatorProcess  
  
    -   傳送埠：PrivateInitiator_To_File  
  
    -   接收埠：File_To_PrivateInitiator  
  
    -   接收位置：File_To_PrivateInitiator  
  
-   PrivateResponderusingFileDrops.xml  
  
    -   協調流程：Microsoft.Solutions.BTARN.PrivateResponder.PrivateResponderProcess  
  
    -   傳送埠：PrivateResponder_To_File  
  
    -   接收埠：File_To_PrivateResponder  
  
    -   接收位置：File_To_PrivateResponder  
  
 下述程序描述如何使用 BTSTask 命令從繫結檔案匯入繫結。 如需詳細資訊，請參閱 BizTalk Server 說明中的"< ImportBindings 命令 > 主題。  
  
## <a name="procedure"></a>程序  
  
#### <a name="to-set-up-btarn-by-using-file-drop-folders"></a>使用檔案放置資料夾設定 BTARN  
  
1.  開啟 [BizTalk 總管]。  
  
2.  停止 PrivateInitiator_To_LOB 和 PrivateResponder_To_LOB 這兩個 LOB SQL 傳送埠。  
  
3.  停用 LOB_To_PrivateInitiator 和 LOB_To_PrivateResponder 這兩個 LOB SQL 接收埠。  
  
4.  取消登錄 Microsoft.Solutions.BTARN.PrivateResponder.PrivateResponderProcess。  
  
5.  取消登錄 Microsoft.Solutions.BTARN.PrivateInitiator.PrivateInitiatatorProcess。  
  
6.  建立 \FileDrops 資料夾，C:\Program Files\Microsoft BizTalk 的 BTARN 資料夾下\<版本\>Accelerator for RosettaNet，然後再建立 \FileDrops 底下的下列資料夾結構：  
  
    -   \PrivateInitiator  
  
         \FromLOB  
  
         \ToLOB  
  
    -   \PrivateResponder  
  
         \FromLOB  
  
         \ToLOB  
  
7.  執行下列命令 (假設 BTARN 安裝在 C: 磁碟機)：  
  
    ```  
    BTSTask ImportBindings /Source:C:\Program Files\Microsoft BizTalk <version> Accelerator for RosettaNet\SDK\FileTransport\PrivateInitiatorusingFileDrops.xml  
    ```  
  
8.  執行下列命令 (假設 BTARN 安裝在 C: 磁碟機)：  
  
    ```  
    BTSTask ImportBindings /Source:C:\Program Files\Microsoft BizTalk <version> Accelerator for RosettaNet\SDK\FileTransport\PrivateResponderusingFileDrops.xml  
    ```  
  
9. 啟動傳送埠：PrivateInitiator_To_File 和 PrivateResponder_To_File。  
  
10. 啟用接收埠：LOB_To_PrivateInitiator 和 LOB_To_PrivateResponder。  
  
## <a name="see-also"></a>請參閱  
 [傳訊範例](../../adapters-and-accelerators/accelerator-rosettanet/messaging-samples.md)