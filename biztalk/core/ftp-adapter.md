---
title: FTP 配接器 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- FTP adapters
ms.assetid: 878dc0b0-d1d8-405a-a697-654dd18ba08e
caps.latest.revision: 11
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ffc72b5166f8971392b41f275338bde593d325af
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="ftp-adapter"></a>FTP 配接器
FTP 配接器可在 FTP 伺服器與 Microsoft BizTalk Server 之間交換資料，並能整合各種平台上商業實務應用程式中儲存的重要資料。 配接器可以連接到 FTP 伺服器透過 SOCKS4 或 SOCKS5 proxy 伺服器。  
  
 FTP 配接器可以將大量檔案從 FTP 伺服器傳輸到 BizTalk Server； 也可以將檔案當作協調流程的一部分來傳輸。  
  
 FTP 配接器是由兩個配接器所組成 — 接收配接器和傳送配接器。  

本節將描述 FTP 接收與傳送配接器，以及安全性和最佳作法資訊。  
  
 ## <a name="receive-adapter"></a>接收配接器  
  
 FTP 接收配接器可讓您將資料從 FTP 伺服器，以移動[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]。 主要功能包括：  
  
-   視需要從 FTP 伺服器提取檔案  
  
-   根據可以設定的排程執行輪詢  
  
-   輪詢 FTP 伺服器，及直接傳送資料[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]  
  
-   指定 FTP 伺服器為 IP 位址、連接埠、密碼和主控件名稱  
  
-   保證檔案傳遞  
  
     FTP 接收配接器也可搭配[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台 」 和 「 BizTalk 總管 中設定及管理每個接收函式，是由下列組態項目所組成：  
  
-   執行 FTP 命令的輪詢間隔 (例如，60 分鐘)  
  
-   路由傳送文件以指定 BizTalk 傳送埠或接受位置的資料  
  
> [!NOTE]
>  FTP 接收配接器不支援接收來自分割資料集的檔案。  
  
## <a name="send-adapter"></a>傳送配接器  
  
 FTP 傳送配接器可讓您將資料從移動[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]至 FTP 伺服器。 主要功能包括：  
  
-   視需要執行傳送的功能  
  
-   保證傳遞  
  
## <a name="supported-platforms"></a>支援的平台  
存取儲存在 FTP 伺服器上任何下列平台的資訊：  

- [!INCLUDE[btsWinSvrNoVersion_md](../includes/btswinsvrnoversion-md.md)] 2016

- [!INCLUDE[btsWinSrv2k12_md](../includes/btswinsrv2k12-md.md)] R2
  
-   [!INCLUDE[btsWinSrv2k12](../includes/btswinsrv2k12-md.md)]  
  
-   [!INCLUDE[btsWinSvr2k8R2](../includes/btswinsvr2k8r2-md.md)]  
  
-   [!INCLUDE[btsWinSvrNoVersion](../includes/btswinsvrnoversion-md.md)] 2008  
  
-   [!INCLUDE[btsWinSvr2k3](../includes/btswinsvr2k3-md.md)]  
  
-   [!INCLUDE[btsWinSvrNoVersion](../includes/btswinsvrnoversion-md.md)]2000 Service Pack 3 (SP3) 和更新版本  
  
-   Sun Solaris 9.0  
  
-   HP-UX  
  
-   LINUX (Redhat 7.x)  
  
-   IBM z/OS v1.9 (MVS)  
  
-   執行 MVS 的 IBM o/S 390  
  
-   AS / 400 OS/400 V5R1  
  
-   i5/OS V5R4 (AS400)  
  
-   i5/OS V6R1 (AS400)  
  
-   GXS ICS  
  
-   AIX  
  
 支援所有的服務組件，除非已特別列出 service pack。  
  
## <a name="in-this-section"></a>本節內容  
  
[最佳做法和建議，FTP 配接器](../core/best-practices-and-recommendations-for-the-ftp-adapter.md)  

[設定 FTP 配接器](../core/configuring-the-ftp-adapter.md)  

[FTP 配接器屬性結構描述和屬性](../core/ftp-adapter-property-schema-and-properties.md)