	public static String getDateFormatCustom1(int timestamp) {
		if (timestamp <= 0) {
			return TODAY;
		}
		Date now = new Date();
		Calendar calendar = Calendar.getInstance();
		long times = timestamp * 1000L;
		calendar.setTimeInMillis(times);

		int nowDays = DateUtil.getDaysByDate(now);
		int timestampDays = DateUtil.getDaysByDate(calendar.getTime());
		int days = nowDays - timestampDays;
		int nowTimestamp = DateUtil.getTimestampNow();
		int difSecond = nowTimestamp - timestamp;
		int difHour = difSecond / 3600;
		if (days == 0 && difHour < 24) {
			return TODAY;
		}
		if (days == 1 && difHour < 48) {
			return YESTERDAY;
		}
		if (now.getYear() != calendar.getTime().getYear()) {
			return DateUtil.getDate(calendar.getTime(), "yy/MM/dd");
		} else {
			return DateUtil.getDate(calendar.getTime(), "MM/dd");
		}

	}
