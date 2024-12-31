CC ?= gcc
BUILD_DIR := build

# Create build directory if it doesn't exist
$(shell mkdir -p $(BUILD_DIR))

all: $(BUILD_DIR)/reg_rw $(BUILD_DIR)/dma_to_device $(BUILD_DIR)/dma_from_device $(BUILD_DIR)/performance $(BUILD_DIR)/test_chrdev

$(BUILD_DIR)/dma_to_device: $(BUILD_DIR)/dma_to_device.o
	$(CC) -lrt -o $@ $< -D_FILE_OFFSET_BITS=64 -D_GNU_SOURCE -D_LARGE_FILE_SOURCE

$(BUILD_DIR)/dma_from_device: $(BUILD_DIR)/dma_from_device.o
	$(CC) -lrt -o $@ $< -D_FILE_OFFSET_BITS=64 -D_GNU_SOURCE -D_LARGE_FILE_SOURCE

$(BUILD_DIR)/performance: $(BUILD_DIR)/performance.o
	$(CC) -o $@ $< -D_FILE_OFFSET_BITS=64 -D_GNU_SOURCE -D_LARGE_FILE_SOURCE

$(BUILD_DIR)/reg_rw: $(BUILD_DIR)/reg_rw.o
	$(CC) -o $@ $<

$(BUILD_DIR)/test_chrdev: $(BUILD_DIR)/test_chrdev.o
	$(CC) -o $@ $<

$(BUILD_DIR)/%.o: %.c
	$(CC) -c -std=c99 -o $@ $< -D_FILE_OFFSET_BITS=64 -D_GNU_SOURCE -D_LARGE_FILE_SOURCE

clean:
	rm -rf $(BUILD_DIR)