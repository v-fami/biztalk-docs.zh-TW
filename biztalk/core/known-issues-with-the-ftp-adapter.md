---
title: "FTP 配接器的已知問題 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9e58f2db-9ec5-41fe-af02-9a7d60a217db
caps.latest.revision: "17"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 4c12b6f1693fe475a1b123a6163a11b35fd96932
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="known-issues-with-the-ftp-adapter"></a>FTP 配接器的已知問題
本節包含可幫助您避免錯誤的資訊。  
  
## <a name="known-issues"></a>已知問題  
  
#### <a name="data-may-be-duplicated-or-lost-when-you-receive-data-in-biztalk-server-by-using-the-ftp-adapter"></a>當您使用 FTP 配接器在 BizTalk Server 中接收資料時，資料可能會重複或遺失。  
  
##### <a name="problem"></a>問題  
 當您使用 FTP 配接器在 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 中接收資料時，資料可能會重複或遺失。  
  
##### <a name="cause"></a>原因  
 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] FTP 配接器使用 FTP 用戶端通訊協定輪詢指定的 FTP 伺服器，並依資料的「原貌」從伺服器擷取資料。 FTP 配接器不會驗證其所擷取的任何資料。 FTP 配接器會將擷取的文件傳送到 BizTalk 傳訊引擎以進行處理，然後會從 FTP 伺服器刪除原始的文件。 如果 FTP 配接器從正在由主控件應用程式寫入的 FTP 伺服器擷取文件，則擷取的文件會不完整。 如果 FTP 配接器擷取不完整的原始文件複本，下列實例中可能會發生資料重複或資料遺失的情況：  
  
-   如果原始文件正由主控件應用程式寫入 FTP 伺服器，FTP 配接器就無法刪除該文件，且會在為接收位置所設定的下一個輪詢間隔擷取該文件的另一個複本。 這個行為將導致文件重複。  
  
-   如果主控件應用程式已完成將文件寫入 FTP 伺服器，該文件將被刪除。 這個行為將導致資料遺失。  
  
##### <a name="resolution"></a>解決方案  
 若要解決這個行為，請使用下列其中一個方法：  
  
-   設定主控件應用程式寫入與公用 FTP 資料夾同一硬碟上的暫存資料夾，並定期將暫存資料夾的內容移至 FTP 資料夾。 暫存資料夾應位於與公用 FTP 資料夾相同的硬碟上，以確定移動作業為不可部分完成。 不可部分完成的作業就是不可分別運作的作業。 如果您使用 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] FTP 配接器寫入資料到公用 FTP 資料夾，則可在設定傳送埠時，在 [FTP 傳輸屬性] 對話方塊中指定暫存資料夾屬性來執行上述動作。 如果您指定暫存資料夾屬性，請確定此資料夾位於與公用 FTP 資料夾相同的實體磁碟上。  
  
-   當主控件應用程式沒有寫入資料到 FTP 伺服器時，設定 FTP 接收位置在服務窗口中作業。 您可在設定接收位置屬性時指定服務窗口。  
  
#### <a name="ftp-adapter-does-not-support-revocation-checks-on-the-server-certificates"></a>FTP 配接器不支援對伺服器憑證進行撤銷檢查  
  
##### <a name="problem"></a>問題  
 [!INCLUDE[prague](../includes/prague-md.md)] 中的 FTP 配接器經過增強，可以支援使用 SSL/TLS 來與 FTPS 伺服器往返進行安全的檔案傳輸。 憑證撤銷清單 (CRL) 包含已經撤銷而不再有效之憑證的清單。 FTP 配接器不會查看 CRL 來驗證伺服器憑證。  
  
##### <a name="cause"></a>原因  
 依照 設計，FTP 配接器在接受伺服器憑證之前，並不會查看 CRL 。  
  
##### <a name="resolution"></a>解決方案  
 不需動作，此行為是經過設計的。  
  
#### <a name="ftp-adapter-downloads-files-larger-than-max-file-size"></a>FTP 配接器會下載超過最大檔案大小的檔案  
  
##### <a name="problem"></a>問題  
 FTP 接收配接器會從下列 FTP 伺服器下載大小超過指定之 [最大檔案大小] 屬性的檔案：  
  
-   AIX  
  
-   MVS  
  
-   AS400  
  
-   GXS  
  
##### <a name="cause"></a>原因  
 依照設計，FTP 配接器從這些 FTP 伺服器下載檔案之前，並不會注意最大檔案大小。  
  
##### <a name="resolution"></a>解決方案  
 不需動作，此行為是經過設計的。  
  
## <a name="see-also"></a>另請參閱  
 [如何設定 FTP 接收位置](http://msdn.microsoft.com/library/1d8fde35-f787-4a5e-a8bd-8c418d0f75c3)   
 [FTP 配接器疑難排解](../core/troubleshooting-the-ftp-adapter.md)