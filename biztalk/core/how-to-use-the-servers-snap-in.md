---
title: "如何使用伺服器嵌入式管理單元 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4f520692-9606-41f5-98ed-5a4962bd1f09
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 12eb72323a6dcd1132f03febc9b4d9bd75316c84
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-use-the-servers-snap-in"></a>如何使用伺服器嵌入式管理單元
此版本的「企業單一登入」(SSO) 包含 ENTSSO「伺服器嵌入式管理單元」，可讓您透過 Windows 介面對 ENTSSO 伺服器進行檢視、監控以及執行某些動作。  
  
> [!NOTE]
>  如果您的系統有防火牆，而且伺服器名稱使用 FQDN 格式，則您可能無法連線到伺服器。 您必須改為指定 NetBIOS 名稱或相關聯的 IP 位址。  
  
### <a name="to-use-the-entsso-servers-snap-in"></a>若要使用 ENTSSO 伺服器嵌入式管理單元  
  
1.  開啟 [企業單一登入]。  
  
2.  在 [領域] 窗格中，按一下**伺服器**節點。  
  
     [結果] 窗格隨即顯示下列資訊。  
  
    -   **名稱**： 指定的名稱。  
  
    -   **狀態**: ENTSSO 服務 （線上、 離線，暫止狀態，啟動、 停止、 開始擱置、 停止擱置） 的狀態。  
  
    -   **日期**： 取得資訊的日期。  
  
    -   **時間**： 取得資訊的時間。  
  
    -   **SSO 伺服器**： 伺服器的完整的名稱。  
  
    -   **服務帳戶**: ENTSSO 服務帳戶。  
  
    -   **SSO 資料庫**： 與此伺服器進行通訊的 ENTSSO 資料庫。  
  
    -   **密碼伺服器**： 指出是否正在執行的密碼伺服器模組。  
  
    -   **密碼同步**： 指出是否已安裝密碼同步處理。  
  
    -   **電腦**： 電腦的 NETBIOS 名稱。  
  
    -   **事件會計算**： 資訊/警告/錯誤事件計數。 重設此欄位會使計數器從 0 開始。  
  
    -   **安裝的 SSO 版本**: ENTSSO.exe 的版本號碼。 此項資訊也會指出這是 32 位元 (x86) 或 64 位元 (x64)。  
  
### <a name="to-start-or-stop-the-server-service"></a>若要啟動或停止伺服器服務  
  
-   在 ENTSSO 伺服器嵌入式管理單元，以滑鼠右鍵按一下伺服器，然後按一下**啟動**或**停止**。  
  
### <a name="to-display-information-for-one-server"></a>若要顯示某部伺服器的資訊  
  
-   在 [伺服器] 樹狀目錄中，按一下該部伺服器。  
  
     資訊隨即顯示在 [結果] 窗格中。  
  
### <a name="to-add-a-server"></a>若要新增伺服器  
  
-   在 [領域] 窗格中，按一下滑鼠右鍵，然後按一下**新增伺服器**。  
  
     **新增伺服器** 對話方塊隨即出現。 輸入或瀏覽至您要新增的伺服器。  
  
> [!NOTE]
>  在某些工作群組環境中，按一下**瀏覽**按鈕會關閉此對話方塊。 而不是使用**瀏覽**按鈕，只要在方塊中輸入伺服器名稱。  
  
### <a name="to-view-or-change-server-properties"></a>檢視或變更伺服器屬性  
  
-   在伺服器樹狀目錄中，以滑鼠右鍵按一下伺服器，然後按一下**屬性**。  
  
     **伺服器屬性** 對話方塊隨即出現。 您可以檢視或變更下列索引標籤中的資訊：  
  
    -   **稽核層級**  
  
    -   **SSO 資料庫**  
  
    -   **SSO 服務**  
  
    -   **密碼同步**  
  
    -   **進階**